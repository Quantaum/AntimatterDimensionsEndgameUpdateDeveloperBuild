<script>
import DescriptionDisplay from "@/components/DescriptionDisplay";
import EffectDisplay from "@/components/EffectDisplay";

export default {
  name: "GalacticPowerRow",
  components: {
    DescriptionDisplay,
    EffectDisplay
  },
  data() {
    return {
      isUnlocked: false
    };
  },
  computed: {
    config() {
      return GalacticPowers.config;
    },
    title() {
      return `Galactic Power ${this.config.id}`;
    }
  },
  methods: {
    update() {
      this.isUnlocked = this.config.isUnlocked;
    }
  }
};
</script>

<template>
  <div v-show="isUnlocked">
    <DescriptionDisplay
      :config="config.reward"
      title="title"
    />
    <EffectDisplay
      :config="config.reward"
    />
  </div>
</template>

<style scoped>

</style>
