<template>
  <div class="single-card">
    <img
      :src="
        'https://www.pokecardex.com/assets/images/sets/FST/HD/' + img + '.jpg'
      "
    />
    <CardCounter @modifyCount/>
  </div>
</template>

<script>
import CardCounter from "./CardCounter";
export default {
  props: {
    img: {
      type: Number,
    },
  },
  components: {
    CardCounter,
  },
  methods: {
    modifyCount(modification) {
      this.$emit("modifyCount", this.modification);
    },
  },
};
</script>

<style lang="scss" scoped>
.single-card {
  margin: 10px;
  position: relative;
}
img {
  border-radius: 19px;
  width: 200px;
}
</style>
