<template>
  <div class="container">
    <div class="sidebar-container">
      <TheSidebar
        :timeFrame="currentTimeFrame"
        @changed-timeFrame="$event => currentTimeFrame = $event"
      />
    </div>
    <div class="cards-container">
      <DashboardCard
        v-for="timeFrame in timeFrames" :key="timeFrame.title"
        :timeFrame="timeFrame"
        :period="currentTimeFrame ? currentTimeFrame : 'daily'"
        :imageSrc="`./assets/images/job.svg`"
      />
    </div>
  </div>
</template>

<script>
import DashboardCard from './components/DashboardCard.vue'
import TheSidebar from './components/TheSidebar.vue'
import { timeFrames } from './assets/data';

export default {
  name: 'App',
  components: {
    DashboardCard,
    TheSidebar
  },
  data() {
    return {
      currentTimeFrame: null
    }
  },
  computed: {
    timeFrames() {
      return timeFrames
    }
  }
}
</script>

<style lang="scss">
@import './assets/colors.scss';

body {
  height: 100vh;
  width: 100vw;
  align-content: center;
  margin: 0;
  background-color: $very-dark-blue;
}

#app {
  font-family: 'Rubik';
  font-size: 14px;
  font-weight: 300;
  color: white;
  text-align: center;
  display: flex;
  justify-content: center;
}

.container {
  width: 1000px;
  margin: 0 40px;
  display: flex;
}

.sidebar-container {
  flex: 0 0 25%;
}

.cards-container {
  flex: 0 0 75%;
  display: flex; 
  flex-wrap: wrap;
}

</style>
