<template>
  <div>
    <SearchInput v-model="searchKeyword" @search="searchProducts" />
    <main>
      <ul class="product__list">
        <li
          v-for="item in products"
          :key="item.id"
          class="product__item">
          <nuxt-link :to="`/detail/${item.id}`" class="product__link">
            <picture class="product__img">
              <img :src="item.imageUrl" :alt="item.name">
            </picture>
          </nuxt-link>
          <strong class="product__name">{{ item.name }}</strong>
          <strong class="product__price">{{ item.price }}</strong>
        </li>
      </ul>
    </main>
  </div>
</template>

<script>
import axios from 'axios'
import {fetchProductsByKeyword} from '@/api'
import SearchInput from '@/components/SearchInput'
// import ProductList from '@/components/ProductList'
export default {
  components: { SearchInput },
  async asyncData() {
    const response = await axios.get('http://localhost:3000/products')
    const products = response.data.map((item) => {
      return {
        ...item,
        imageUrl: `${item.imageUrl}?random=${Math.random()}`,
      }
    })
    return { products }
  },
  data () {
    return {
      searchKeyword: ''
    }
  },
  methods: {
    async searchProducts() {
      const response = await fetchProductsByKeyword(this.searchKeyword)
      this.products = response.data.map((item) => {
        return {
          ...item,
          imageUrl: `${item.imageUrl}?random=${Math.random()}`,
        }
      })
    }
  }
}
</script>
<style lang="scss" scoped>
.product {
  &__list {
    display: flex;
    flex-wrap: wrap;
    padding: 0;
    margin: 0 -0.5%;
  }
  &__item {
    flex: 0 0 49%;
    margin: 0.5%;
  }
  &__link {
    display: block;
    position: relative;
    padding-bottom: 75%;
    background-color: #e9e9e9;
  }
  &__img {
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    > source,
    > img {
      display: block;
      position: absolute;
      top: 0;
      width: 100%;
      height: 100%;
    }
  }
  &__name,
  &__price {
    display: block;
    text-align: center;
  }
  &__name {
    margin-top: .75rem;
  }
  &__price {
    margin-top: .25rem;
    font-size: 1.25rem;
  }
}
@media screen and (min-width: 768px) {
  .product {
    &__item {
      flex: 0 0 24%;
    }
  }
}
</style>
