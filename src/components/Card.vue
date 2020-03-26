<template>
  <div
    class="card"
    :class="{
      card__active: card.active,
      card__selected: selected
    }"
  >
    <card-front :card="card" @click.native="toggleCard({ card })" />
    <card-back :card="card" />
  </div>
</template>

<script>
import { mapMutations } from 'vuex'
import CardFront from './CardFront.vue'
import CardBack from './CardBack.vue'
export default {
  components: {
    CardFront,
    CardBack
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
    ...mapMutations(['toggleCard']),
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
.card__active {
  .card_back {
    transform: scale(1);
    opacity: 1;
  }
  .card_front {
    transform: translate3d(0, -100px, 0);
  }
}
</style>