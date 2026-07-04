<script>
import BlobSnowflakes from "@/components/BlobSnowflakes";
import Hadrons from "@/components/tabs/large-hadron-collider/Hadrons";
import TachyonParticles from "@/components/tabs/time-dilation/TachyonParticles";

export default {
  name: "BackgroundAnimations",
  components: {
    BlobSnowflakes,
    Hadrons,
    TachyonParticles
  },
  data() {
    return {
      blob: false,
      animateHadrons: false,
      animateTachyons: false
    };
  },
  methods: {
    update() {
      this.blob = Theme.currentName() === "S11";
      this.animateHadrons = player.options.animations.hadrons &&
        Tabs.current[this.$viewModel.subtab].name === "Large Hadron Collider";
      this.animateTachyons = player.options.animations.tachyonParticles &&
        Tabs.current[this.$viewModel.subtab].name === "Time Dilation";
    }
  },
};
</script>

<template>
  <div
    id="ui-background-animations"
    class="l-background-animations"
  >
    <BlobSnowflakes v-if="blob" />
    <Hadrons v-if="animateHadrons" />
    <TachyonParticles v-if="animateTachyons" />
  </div>
</template>

<style scoped>

</style>
