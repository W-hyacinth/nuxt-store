<template>
  <header class="shop__header">
    <h1 class="shop__logo"><nuxt-link to="/">Nuxt Shopping</nuxt-link></h1>
  </header>
</template>
<script>
export default {
}
</script>
<style lang="scss" scoped>
.shop__logo {
  text-align: center;
  .nuxt-link-active {
    color: #00c58e;
    text-decoration: none;
  }
}
</style>
