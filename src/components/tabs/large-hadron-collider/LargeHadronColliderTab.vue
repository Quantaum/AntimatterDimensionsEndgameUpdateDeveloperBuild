<script>
import AcceleratorsPanel from "./AcceleratorsPanel";

export default {
  name: "LargeHadronColliderTab",
  components: {
    AcceleratorsPanel
  },
  data() {
    return {
      hasAccelerator: false
    };
  },
  methods: {
    update() {
      this.hasAccelerator = Accelerators.all.some(a => a.isUnlocked);
    },
  }
};
</script>

<template>
  <div class="l-large-hadron-collider-tab">
    <div class="l-large-hadron-collider-all-content-container">
      <AcceleratorsPanel v-if="hasAccelerator" />
      <div v-if="!hasAccelerator">
        Reach {{ format(Decimal.pow10(1e200), 2, 2) }} Antimatter
      </div>
    </div>
  </div>
</template>

<style scoped>
.l-large-hadron-collider-tab {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.l-large-hadron-collider-all-content-container {
  display: flex;
  flex-direction: column;
  width: 100%;
  align-items: center;
}
</style>
