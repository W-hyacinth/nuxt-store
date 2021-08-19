<template>
  <section class="">
    <h2 class="ally">검색영역</h2>
    <div class="search__field">
      <input type="text" :value="value" placeholder="검색어를 입력하세요" @input="$emit('input', $event.target.value)">
      <button type="submit" @click.prevent="$emit('search')">검색</button>
    </div>
  </section>
</template>
<script>
export default {
  props: {
    value: {
      type: String,
      default: () => { return '' }
    }
  }
}
</script>
<style lang="scss" scoped>

</style>
