<template>
  <div :class="['key', span ? 'span' : '', active ? 'active' : '']">
    <div className="side" />
    <div className="top" />
    <div className="char">{{ char }}</div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Key'
}
</script>

<script lang="ts" setup>
import { ref } from 'vue'
import sound from './keyboard.mp3'

const props = defineProps<{
  char: string
  span?: boolean
}>()

const active = ref(false)

function useSound() {
  const audio = ref(new Audio(sound))
  return {
    play: () => audio.value.play(),
    stop: () => {
      audio.value.pause()
      audio.value.currentTime = 0
    }
  }
}

document.addEventListener('keydown', e => {
  active.value = e.key === props.char
  useSound().stop()
  useSound().play()
})

document.addEventListener('keyup', () => {
  active.value = false
})
</script>
