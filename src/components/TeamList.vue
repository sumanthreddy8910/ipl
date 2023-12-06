<template>
  <div class="team-list">
    <div 
      v-for="team in teams" 
      :key="team['Team Name']" 
      class="flip-card" 
      @click="flipCard(team['Team Name'])"
    >
      <div class="flip-card-inner" :class="{ flipped: flippedCards.includes(team['Team Name']) }">
        <div 
          class="flip-card-front" 
          :style="{ backgroundColor: team['Colour Code'] }"
        >
          
          <div class="flip-card-front-bottom" :style="{ backgroundColor: '#2B303B' }">
          <h3 class="team-name">{{ team['Team Name'] }}</h3>
          </div>
        </div>
        <div class="flip-card-back">
          <TeamDetails :team="team" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TeamDetails from './TeamDetails.vue';

export default {
  name: 'TeamList',
  components: {
    TeamDetails
  },
  props: {
    teams: Array
  },
  data() {
    return {
      flippedCards: []
    };
  },
  methods: {
    flipCard(teamName) {
      const index = this.flippedCards.indexOf(teamName);
      if (index === -1) {
        this.flippedCards.push(teamName);
      } else {
        this.flippedCards.splice(index, 1);
      }
    }
  }
};
</script>

<style>
.team-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding: 0 40px; 
  margin: 0 auto; 
  max-width: 1200px; 
}

.flip-card {
  background-color: transparent;
  width: 230px;
  height: 350px;
  perspective: 1000px;
  margin: 10px;
  flex: 0 0 calc(33.333% - 20px);
  position: relative;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  transform-origin: center;
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  display: flex;
  justify-content: center;
  align-items: center; 
  top: 0;
  left: 0;
  flex-direction: column;
}

.team-name {
  text-align: center;
  margin: 0;
}
.flip-card-front {
  position: relative;
  color: black;
  display: flex;
  flex-direction: column;
  justify-content: flex-end; 
  align-items: center;
  overflow: hidden; 
  background-color: var(--team-color); 
}


.flip-card-front::after {
  content: '';
  position: absolute;
  width: 160%; 
  height: 200px; 
  background-color: #2B303B; 
  border-radius: 50%;
  bottom: -50px; 
  left: 50%;
  transform: translateX(-50%);
  z-index: 1;
}

.team-name {
  position: relative;
  color: white; 
  z-index: 2;
  margin-bottom: 60px;
  font-size: 24px;
  font-weight: bold;
}

.flip-card-back {
  background-color: #E2E3E5; 
  color: black; 
  transform: rotateY(180deg);
  
}

.flipped {
  transform: rotateY(180deg);
}

</style>
