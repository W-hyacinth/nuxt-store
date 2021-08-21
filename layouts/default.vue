<template>
  <div>
    <Header />
    <Nuxt />
  </div>
</template>

<script>
import Header from '@/components/Header'
export default {
  components: { Header },
  created() {
  }
}
</script>

<style lang="scss">
.ally {
  border: 0;
  clip: rect(0 0 0 0);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}
ul {
  list-style: none;
  padding: 0;
}
</style>
