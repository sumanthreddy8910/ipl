<template>
  <div id="app">
    <header>
      <h1>IPL Teams</h1>
    </header>
    <TeamList :teams="teams" />
  </div>
</template>


<script>
import TeamList from './components/TeamList.vue';

export default {
  name: 'App',
  components: {
    TeamList
  },
  data() {
    return {
      teams: []
    };
  },
  created() {
    fetch('https://sumanth-reddy.netlify.app/api')
      .then(response => response.json())
      .then(data => {
        console.log(data)
        this.teams = data["IplTeams"];
      });
  }
};
</script>

<style>
#app {
  text-align: center;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}

header {
  background-color: #34495e;
  color: white;
  padding: 10px 0;
  margin-bottom: 20px;
}

header h1 {
  margin: 0;
  padding: 10px;
}
</style>
