<template>
  <div class="card-list" :class="{ 'card-list__selected': !!selected }">
    <ul :style="{ width: `${1 * 100}%`}">
      <li
        v-for="(card, index) in 4"
        :key="index"
        :style="{ transform: `translate3d(-${0 * 100}%, 0, 0)` }"
      >
        {{ card }}
      </li>
    </ul>
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
export default {
  computed: {
    ...mapState(['cards', 'currentIndex', 'selected'])
  },
  data () {
    return {
      selected: false,
    }
  },
  methods: {
    ...mapMutations(['prevCard', 'nextCard', 'selectCard'])
  },
  mounted () {
    let touch = {}
    this.$el.addEventListener('touchstart', evt => {
      touch.startX = evt.touches[0].clientX
      touch.endX = 0
    })
    this.$el.addEventListener('touchmove', evt => {
      touch.endX = evt.touches[0].clientX
    })
    this.$el.addEventListener('touchend', () => {
      if (!touch.endX || Math.abs(touch.endX - touch.startX) < 10) {
        return
      }
      if (touch.endX < touch.startX) {
        this.selected = true
      } else {
        this.selected = false
      }
    })
  }
}
</script>

<style lang="scss">
.card-list {
  margin: 30px;
  height: 300px;
  border: 1px solid gray;
  transform: scaleX(1);
  transition: all 0.6s ease;

  ul {
    display: flex;
    height: 100%;
  }
  li {
    flex: 1;
    transition: all 0.6s ease;
  }
}
.card-list__selected {
  transform: scaleX(1.1);
}
</style>