<template>
  <div>
    <div class="counter" @mouseenter="isHover=true" @mouseleave="isHover = false">
      <QuantityChangeButton v-if="isHover" @modifyCount="modifyCount" :modification="'minus'"/>
      <div class="count_value">{{count}}</div>
      <QuantityChangeButton v-if="isHover" @modifyCount="modifyCount" :modification="'plus'" />
    </div>
  </div>
</template>

<script>
import QuantityChangeButton from "./QuantityChangeButton.vue";
export default {
  components: { QuantityChangeButton },
  data() {
      return {
          isHover: false,
          count: 0,
      }
  },
  props: {
      count: {
          type: Number,
      },
  },
  methods: {
      modifyCount(modification) {
                this.$emit("modifyCount", this.modification);
      }
  },
};
</script>

<style lang="scss" scoped>
.counter {
  background: rgba(0, 0, 0, 0.8);
  color: white;
  border-radius: 0 0 19px 19px;
  position: absolute;
  width: 100%;
  bottom: 0;
  transition: 0.6s;
  height:50px;

  display: flex;
  justify-content: center;

  &:hover {
    border-radius: 19px 19px 19px 19px;
    height: 100%;
  }
}
.count_value {
    display: flex;
    align-items: center;
}
</style>
