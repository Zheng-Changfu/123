<script setup>
import { ref, computed } from 'vue'
import { get } from 'lodash-es'

let id = 0
const values = ref({
  c: [
    { a: 1 }
  ]
})

const values2 = computed(() => {
  /**
   * add 
   *  1,2
   * 
   * add 
   *  1,2,3
   *  3,4,5
   *  4,5,6
   */
  return values.value.c.map(item => ({
    ...item,
    id: ++id
  }))
})


function add() {
  values.value.c.push({ a: 2 })
}


</script>
<template>
  <button @click="add">add</button>
  <button @click="() => console.log(values2)">log</button>
  <div v-for="item in values2">{{ item.a }}</div>
</template>
