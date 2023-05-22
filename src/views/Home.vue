<template>
  <main>
    <h1>Home</h1>
    <input type="text" name="search" v-model="search" />
    <p>search term - {{ search }}</p>
    <div v-for="name in filteredNames" :key="name">{{ name }}</div>
  </main>
</template>

<script>
import { ref, computed, watch, watchEffect } from 'vue'

export default {
  name: 'Home',
  setup() {
    const search = ref('')
    const names = ref([
      'John',
      'Jane',
      'Joe',
      'Jack',
      'Jill',
      'Jenny',
      'Jesse',
      'Jasmine',
      'Jude',
      'Julia',
      'Julian',
    ])

    watchEffect(() => {
      console.log('wf', search.value)
    })

    const filteredNames = computed(() => {
      return names.value.filter((name) => {
        return name.toLowerCase().includes(search.value.toLowerCase())
      })
    })

    return {
      names,
      search,
      filteredNames,
    }
  },
}
</script>

<style></style>
