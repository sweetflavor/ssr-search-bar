<template>
  <div class="container">
    <select v-model="selected">
      <option disabled value="">Seleccione un elemento</option>
      <option v-for="item in items" :key="item.id">{{ item.title }}</option>
    </select>
    <br>
    <h1>{{selected}}</h1>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data } = await axios.get(`https://jsonplaceholder.typicode.com/posts`)
    
    return { items: data }
  },
  data() {
    return {
      selected: ''
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
}
</style>
