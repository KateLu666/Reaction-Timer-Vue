<template>
  <div class="results">
    <h3>Your reaction time is {{ score }}ms</h3>
    <h2 class="rank">Your rank is {{ rank }}</h2>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 100) {
      this.rank = "Godlike";
    } else if (this.score < 200) {
      this.rank = "Pro";
    } else if (this.score < 300) {
      this.rank = "Average";
    } else if (this.score < 400) {
      this.rank = "Beginner";
    } else {
      this.rank = "Newcomer";
    }
  },
};
</script>

<style>
.rank {
  color: #4b7b8b;
  font-weight: bold;
}
</style>
