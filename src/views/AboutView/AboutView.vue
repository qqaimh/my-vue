<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div>
      Count: {{ count}}
      <button @click="increment">increment</button>
    </div>
  </div>
</template>

<script src="./AboutView.js">
// export default {
//   data() {
//     return {
//       count: 0
//     }
//   },
//   methods: {
//     increment() {
//       this.count++
//     }
//   },
//   mounted() {
//     // 在其他方法或是生命周期中也可以调用方法
//     this.increment()
//   }
// }
</script>

<style src="./AboutView.css"></style>
