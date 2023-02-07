<script>
export default {
  data() {
    return {
      teams: []
    }
  },

  async mounted() {
    const result = await fetch("https://api.codetabs.com/v1/proxy/?quest=https://api.kingsleague.dev/teams");
    const teams = await result.json();

    this.teams = teams;
  }
}

</script>

<template>
  <h1>Equipos</h1>

  <div>
    <ul>
      <li v-for="team in teams" :key="team.id">
        <RouterLink :to="'/team/' + team.id">
          <img :src="team.image" :alt="team.name" width="200">
        </RouterLink>
      </li>
    </ul>
  </div>
</template>
