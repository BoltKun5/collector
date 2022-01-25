<template>
  <div class="main-list">
    <SearchComponent />
    <div class="card-list">
      <Card />
      <Card />
      <Card />
    </div>
  </div>
</template>

<script>
import SearchComponent from "./SearchComponent.vue";
import Card from "./Card.vue";
export default {
    components: {
        SearchComponent,
        Card
    }
};
</script>

<style lang="scss" scoped>
.main-list {
  background: rebeccapurple;
  flex: 1;
}
.card-list {
    width: 90%;
    margin: 0 auto;
}
</style>
