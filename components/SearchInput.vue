<template>
  <section class="">
    <h2 class="ally">검색영역</h2>
    <div class="search__field">
      <input type="text" :value="value" class="search__input" placeholder="검색어를 입력하세요" @input="$emit('input', $event.target.value)">
      <button type="submit" class="search__btnSubmit" @click.prevent="$emit('search')">검색</button>
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
.search {
  &__field {
    display: flex;
    justify-content: center;
  }
  &__input {
    padding: 5px 10px;
    font-size: 16px;
    border: 1px solid #ccc;
  }
  &__btnSubmit {
    padding: 5px 10px;
    font-size: 16px;
    color: #fff;
    background-color: #000;
    appearance: none;
    border: 0;
  }
}
</style>
