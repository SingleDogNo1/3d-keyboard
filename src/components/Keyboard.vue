<template>
  <div class="keyboard">
    <div class="column">
      <div class="row" v-for="(row, i) in keys" :key="i">
        <Key v-for="key in row" :key="key" :char="key" :span="key === '0'" />
      </div>
    </div>

    <div class="column">
      <Key v-for="n in ['+', '-']" :key="n" :char="n" span />
    </div>

    <div class="shade" />
    <div class="cover" />
  </div>
</template>

<script lang="ts">
export default {
  name: 'Keyboard'
}
</script>

<script lang="ts" setup>
import { ref } from 'vue'
import Key from './Key.vue'

const keys = ref([
  ['7', '8', '9'],
  ['4', '5', '6'],
  ['1', '2', '3'],
  ['0', '.']
])
</script>
