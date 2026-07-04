<script>
import Hadron from "./Hadron";

export default {
  name: "Hadrons",
  components: {
    Hadron
  },
  data() {
    return {
      count: 0,
      initialized: false,
      bounds: {
        x: 0,
        y: 0
      },
      isBlob: false,
    };
  },
  mounted() {
    this.$nextTick(this.updateSize);
    window.addEventListener("resize", this.updateSize);
    this.initialized = true;
  },
  destroyed() {
    window.removeEventListener("resize", this.updateSize);
  },
  methods: {
    update() {
      this.count = Math.floor(Math.min(player.celestials.laitela.hadrons.total, 100) *
        Math.max(Math.log10(player.celestials.laitela.hadrons.total) / 2, 1));
      this.isBlob = Theme.currentName() === "S11";
    },
    updateSize() {
      this.bounds.x = this.$el.clientWidth;
      this.bounds.y = this.$el.clientHeight;
    }
  }
};
</script>

<template>
  <svg
    v-if="initialized"
    class="c-tachyon-particle-container"
  >
    <Hadron
      v-for="i in count"
      :key="i"
      :bounds="bounds"
      :is-blob="isBlob"
    />
  </svg>
</template>

<style scoped>

</style>
