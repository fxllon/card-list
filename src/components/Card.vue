<template>
  <div
    class="card"
    :class="{
      card__active: card.active,
      card__selected: selected
    }"
  >
    <card-front :card="card" />
  </div>
</template>

<script>
import CardFront from './CardFront.vue'
export default {
  components: {
    CardFront,
  },
  props: {
    card: {
      type: Object
    },
    selected: {
      type: Boolean
    }
  },
  methods: {

  }
}
</script>

<style lang="scss">
.card {
  width: 100%;
  height: 100%;
}
.card__selected {
  visibility: hidden;
}
</style>