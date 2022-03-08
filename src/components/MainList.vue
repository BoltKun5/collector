<template>
  <div class="main-list">
    <SearchComponent @updateFilters="updateFilters" />
    <div class="card-list">
      <Card
        v-for="(card, index) in filteredArray"
        :img="card.id"
        :key="card.id"
        :count="card.quantity"
        @addOne="addOne(index)"
        @removeOne="removeOne(index)"
      />
    </div>
  </div>
</template>

<script>
import SearchComponent from "./SearchComponent.vue";
import Card from "./Card.vue";
import json from "../data.json";

export default {
  components: {
    SearchComponent,
    Card,
  },
  data() {
    return {
      cards: json,
      filters: {
        rarities: ["common", "uncommon", "rare", "holo", "ur", "secrete"],
        name: "",
      },
    };
  },
  computed: {
    filteredArray() {
      return this.cards.filter((card) => {
        return this.filters.rarities.includes(card.rarity);
      });
    },
  },
  methods: {
    addOne(id) {
      this.cards[id].quantity++;
    },
    removeOne(id) {
      this.cards[id].quantity--;
      if (this.cards[id].quantity < 0) this.cards[id].quantity = 0;
    },
    updateFilters(newFilters) {
      this.filters = newFilters;
    },
  },
};
</script>

<style lang="scss" scoped>
.main-list {
  width: 100%;
}
.card-list {
  background: rebeccapurple;
  display: flex;
  flex-wrap: wrap;
  padding: 0 20px;
}
</style>
