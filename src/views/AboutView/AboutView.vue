<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div>
      Count: {{ state.count }}
      <button @click="increment">increment</button>
      
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive } from 'vue'

const state = reactive({ count: 0 })

function increment() {
  state.count++
}
</script>

<script  lang="ts"></script>

<style src="./AboutView.css"></style>
