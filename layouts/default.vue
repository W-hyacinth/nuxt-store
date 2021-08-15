<template>
  <div>
    <header>
      <h1>{{ $route.name }} 페이지</h1>
      <nuxt-link to="/">index</nuxt-link>
    </header>
    <Nuxt />
  </div>
</template>

<script>
export default {
  created() {
  }
}
</script>

<style>

</style>
