<template>
  <div
    class="main-list"
    :style="`background: url('${require('@/assets/background.jpeg')}')`"
  >
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
import Card from "./Card/Card.vue";
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
  //     if (searchInput.value === '') {
  //   return props.items;
  // }

  // const regex = new RegExp(/\s/g);
  // const searchText = searchInput.value.replace(regex, '').toLowerCase();
  // return props.items.filter((item) => {
  //   const cleanLabel = item.label.replace(regex, '').toLowerCase();
  //   return cleanLabel.includes(searchText);
  // });
    filteredArray() {
      return this.cards.filter((card) => {
        let isSearchedName;
         if (this.filters.name === '') {
           isSearchedName = true;
         }
          const regex = new RegExp(/\s/g);
          const searchText = this.filters.name.replace(regex, '').toLowerCase();

          const cleanLabel = card.name.replace(regex, '').toLowerCase();
          isSearchedName = cleanLabel.includes(searchText);

        return (this.filters.rarities.includes(card.rarity) && isSearchedName);
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
  display: flex;
  flex-wrap: wrap;
  padding: 0 20px;
}
</style>
