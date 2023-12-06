<template>
  <div class="team-details">
    <h2>{{ team['Team Name'] }}</h2>
    <p>Captain: {{ team.Captain }}</p>
    <p>Team Colour: {{ team['Team Colour'] }}</p>
    <p>City Based In: {{ team['City Based In'] }}</p>
    <p>Championships Won: {{ team['No. of Championships Won'] }}</p>
    <p>Highest Score: {{ team['Highest Score in an Innings'] }}</p>
  </div>
</template>

<script>
export default {
  name: 'TeamDetails',
  props: {
    team: Object
  }
};
</script>
