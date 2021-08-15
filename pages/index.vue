<template>
  <div>
    <div>
      <input type="text">
    </div>
    <main>
      <ul>
        <li v-for="(item, index) in products" :key="item.id" :index="index">
          <img :src="item.imageUrl" :alt="item.name">
          <strong>{{ item.name }}</strong>
          <strong>{{ item.price }}</strong>
        </li>
      </ul>
    </main>
  </div>
</template>

<script>
import axios from 'axios'
// import ProductList from '@/components/ProductList'
export default {
  async asyncData() {
    const response = await axios.get('http://localhost:3000/products')
    const products = response.data.map((item) => {
      return {
        ...item,
        imageUrl: `${item.imageUrl}?random=${Math.random()}`,
      }
    })
    return { products }
  }
}
</script>
