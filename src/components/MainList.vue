<template>
  <div class="main-list">
    <SearchComponent />
    <div class="card-list">
      <Card v-for="img in 100" :img="img" :key="img" @ />
    </div>
  </div>
</template>

<script>
import SearchComponent from "./SearchComponent.vue";
import Card from "./Card.vue";

export default {
  components: {
    SearchComponent,
    Card,
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    modifyCount() {
      if (modification === "plus") {
        this.count++;
      } else {
        this.count--;
        if (this.count < 0) {
          this.count = 0;
        }
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.main-list {
}
.card-list {
  background: rebeccapurple;
  justify-content: center;
  display: flex;
  flex-wrap: wrap;
}
</style>
