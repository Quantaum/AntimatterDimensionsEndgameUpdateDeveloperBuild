<script>
import GalacticPowerRow from "./GalacticPowerRow";

export default {
  name: "GalacticPowerTab",
  components: {
    GalacticPowerRow
  },
  data() {
    return {
      galacticPower: new Decimal(),
      nextPow: 0
    };
  },
  computed: {
    powers() {
      return GalacticPowers.all;
    },
    rows() {
      return Math.ceil(this.powers.length);
    },
    nextAtDisplay() {
      const first = this.nextPow?.id === 1;
      const next = GalacticPower.nextPowUnlockGP;

      if (first) return `The first Galactic Power unlocks at ${format(next)} Galactic Power.`;
      return next === undefined
        ? "All Galactic Powers unlocked"
        : `Next Galactic Power unlocks at ${format(next)} Galactic Power.`;
    }
  },
  methods: {
    update() {
      this.galacticPower.copyFrom(Currency.galacticPower.value.floor());
      this.nextPow = GalacticPower.nextPow;
    },
    getPower(row, column) {
      return () => this.powers[(row - 1) + column - 1];
    }
  }
};
</script>

<template>
  <div class="l-endgame-milestone-grid">
    <div>You have {{ format(galacticPower, 2, 2) }} Galactic Power.</div>
    <div
      v-for="row in rows"
      :key="row"
      class="l-endgame-milestone-grid__row"
    >
      <GalacticPowerRow
        v-for="column in 1"
        :key="row + column"
        :get-power="getPower(row, column)"
        class="l-endgame-milestone-grid__cell"
      />
    </div>
    <div>{{ nextAtDisplay }}</div>
  </div>
</template>

<style scoped>

</style>
