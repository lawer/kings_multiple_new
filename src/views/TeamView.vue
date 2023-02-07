<template>
  <h1>{{team.name}}</h1>

  <h2>Coach: {{team.coach}}</h2>
  <div>
    <ul>
      <li v-for="player in team.players" :key="player.id">
        {{ player }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: null,
      team: {}
    }
  },
  async mounted() {
    this.id = this.$route.params.id;

    const result = await fetch("https://api.codetabs.com/v1/proxy/?quest=https://api.kingsleague.dev/teams/" + this.id);
    const team = await result.json();

    this.team = team;

  }
}
</script>

<style scoped>

</style>