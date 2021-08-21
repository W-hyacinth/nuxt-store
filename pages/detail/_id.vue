<template>
  <main class="productInfo__main">
    <picture class="productInfo__img">
      <img :src="product.imageUrl" alt="">
    </picture>
    <article class="productInfo__detail">
      <h2 class="productInfo__name">{{ product.name }}</h2>
      <strong class="productInfo__price">{{ product.price }}</strong>
      <button type="button" class="productInfo__btnCart" @click="addToCart">장바구니 담기</button>
    </article>
  </main>
</template>
<script>
import {fetchProductById} from '@/api'

export default {
  async asyncData({ params }) {
    const response = await fetchProductById(params.id)
    const product = response.data
    return { product }
  },
  methods: {
    addToCart() {
      this.$store.commit('addCartItem', this.product)
      const response = confirm('상품을 장바구니에 담았습니다.\n장바구니 페이지로 이동하시겠습니까?')
      if (response) { this.$router.push('/cart') }
    },
  }
}
</script>
<style lang="scss" scoped>
.productInfo {
  &__main {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  &__img {
    flex: 0 0 49%;
    margin: 0.5%;
    position: relative;
    &:before {
      display: block;
      padding-bottom: 75%;
      background-color: #e9e9e9;
      content: "";
    }
    > source,
    > img {
      display: block;
      position: absolute;
      top: 0;
      width: 100%;
      height: 100%;
    }
  }
  &__detail {
    flex: 0 0 49%;
    margin: 0.5%;
  }
  &__price {
    display: block;
    font-size: 1.25rem;
  }
  &__btnCart {
    margin-top: .5rem;
  }
}
</style>
