<template src="./aboutView.html"> 
</template>

<style src="./AboutView.css"></style>

<script lang="ts" setup>
import { reactive, ref } from 'vue'
import AboutItem from '../../components/AboutItem.vue'
import vBackground from '../../directives/vBackground'


const state = reactive({ count: 0 })
const checkedNames = ref([])

function incrementTwo() {
  state.count++
}

const checked = ref(true)
const selected =  ref('')
  
const increment = () => {
  incrementTwo()
}



</script>

