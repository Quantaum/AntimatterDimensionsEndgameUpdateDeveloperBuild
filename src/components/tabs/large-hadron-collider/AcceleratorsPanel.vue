<script>
import wordShift from "@/core/word-shift";
  
import Accelerator from "./Accelerator";

export default {
  name: "AcceleratorsPanel",
  components: {
    Accelerator
  },
  data() {
    return {
      decayRate: 0,
      time: 0,
    };
  },
  computed: {
    accelerators() {
      return Accelerators.all;
    }
  },
  methods: {
    update() {
      this.decayRate = player.endgame.largeHadronCollider.powerCores * 0.00001;
      this.time = Date.now();
    }
  }
};
</script>

<template>
  <div class="l-accelerator-panel-container">
    <div class="c-accelerator-panel-title">
      Accelerators
    </div>
    <div
      class="l-accelerator-content-container"
    >
      Accelerators can be activated by clicking on their bars.
      <span>You cannot activate more than one Accelerator at once.</span>
      When active, Accelerators fill at a rate of {{ formatPercents(decayRate) }} per second.
      <br>
      Accelerator effects apply even when not activated, and are based on the current fill percentage.
      <div class="c-accelerator-bar-container">
        <Accelerator
          v-for="accelerator in accelerators"
          :key="accelerator.config.id"
          :strike="accelerator"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.c-accelerator-bar-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
