<template>
  <div class="about">

    <div>
      Count: {{ state.count }}
      <button @click="increment">increment</button>
      
      <div>
        <input type="checkbox" id="checkbox" v-model="checked" />
        <label for="checkbox">{{ checked }}</label>
      </div>

      <div>
        <div>Selected: {{ selected }}</div>

<select v-model="selected">
  <option disabled value="">Please select one</option>
  <option>A</option>
  <option>B</option>
  <option>C</option>
</select>
      </div>

    </div>

    <div>
      <div>Checked names: {{ checkedNames }}</div>

<input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
<label for="jack">Jack</label>

<input type="checkbox" id="john" value="John" v-model="checkedNames">
<label for="john">John</label>

<input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
<label for="mike">Mike</label>
    </div>
  </div>
</template>

<style src="./AboutView.css"></style>

<script lang="ts" setup>
import { reactive, ref } from 'vue'
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

