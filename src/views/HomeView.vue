<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'

const props = defineProps<{
  foo: string
  bar?: number
}>()
console.log(2222)
</script>

<template>
  <main>
    <TheWelcome />
  </main>
</template>
