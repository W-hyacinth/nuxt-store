<template>
  <div>
    <h2>장바구니</h2>
    <ul class="cartItem__list">
      <li v-for="item in $store.state.cartItems" :key="item.id" class="cartItem__item">
        <nuxt-link :to="`/detail/${item.id}`" class="cartItem__link">
          <picture class="cartItem__img">
            <img :src="item.imageUrl" alt="">
          </picture>
        </nuxt-link>
        <span class="cartItem__info">
          <strong class="cartItem__name">{{ item.name }}</strong>
          <em class="cartItem__price">{{ item.price }}</em>
        </span>
      </li>
    </ul>
    <div class="btn__area">
      <button type="button">구매하기</button>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.cartItem {
  &__list {
    display: flex;
    flex-direction: column;
  }
  &__item {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: .5rem;
    border: 1px solid #ccc;
    border-radius: 3px;
    &:nth-of-type(n+2) {
      margin-top: .5rem;
    }
  }
  &__link {
    flex: 0 0 100px;
    display: block;
    position: relative;
    &:before {
      display: block;
      padding-bottom: 75%;
      background-color: #e9e9e9;
      content: "";
    }
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
  &__info {
    flex: 0 1 100%;
    margin-left: .5rem;
    display: block;
  }
  &__name {
    font-size: 1.25rem;
  }
  &__price {
    display: block;
    margin-top: .5rem;
    font-style: normal;
  }
}
</style>
