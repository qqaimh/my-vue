<template>
  <div class="about">

<div>
  Count: {{ state.count }}
  Sore Count: {{ count }}
  <button @click="increment">increment</button>
  <button @click="resetStore">resetStore</button>
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
<div v-background>111</div>
<AboutItem />
</div>
</template>

<style src="./AboutView.css"></style>

<script lang="ts" setup>
import { reactive, ref, watch } from 'vue'
import AboutItem from '../../components/AboutItem.vue'
import vBackground from '../../directives/vBackground'
import { storeToRefs } from 'pinia'
import { useCounterStore } from '@/stores/counter';
import { useDark, useTitle,useToggle } from '@vueuse/core'


const state = reactive({ count: 0 })
const checkedNames = ref([])

const store = useCounterStore()
// `name` 和 `doubleCount` 是响应式的 ref
// 同时通过插件添加的属性也会被提取为 ref
// 并且会跳过所有的 action 或非响应式 (不是 ref 或 reactive) 的属性
const { count, doubleCount } = storeToRefs(store)
// 作为 action 的 increment 可以直接解构
const { increment } = store

function incrementTwo() {
  state.count++
}

function resetStore() {
  console.log(991)
  store.$reset()
}

const checked = ref(true)
const selected =  ref('')
  
// const increment = () => {
//   incrementTwo()
// }

store.$subscribe((mutation, state) => {
  // import { MutationType } from 'pinia'
  mutation.type // 'direct' | 'patch object' | 'patch function'
  // 和 cartStore.$id 一样
  mutation.storeId // 'cart'
  // 只有 mutation.type === 'patch object'的情况下才可用
  // mutation.payload // 传递给 cartStore.$patch() 的补丁对象。

  // 每当状态发生变化时，将整个 state 持久化到本地存储。
  console.log(992, mutation, state)
})

const title = useTitle('Set title')
watch(count, () => {
    title.value = count.value >3 ? '🌙 Good evening!' : '☀️ Good morning!'
})



</script>

