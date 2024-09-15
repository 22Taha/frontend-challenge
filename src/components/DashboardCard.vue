<template>
  <div class="main-wrapper">
    <div class="first-class" :class="`bg-${timeFrame.title}`">
      <img class="image" :src="getImageSrc" :alt="getTitle + 'image'">
    </div>
    <div class="second-class">
      <div class="second-class-title">
        <b>
          {{ getTitle }}
        </b>
        <div class="three-dots-btn">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
      <div class="current">
        <span>
          {{ currentCount }}
        </span>
        <p>
          Completed
        </p>
      </div>
      <div class="last">
        Last {{ getPeriod }}: {{ lastCount }} Completed
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'DashboardCard',
  props: {
    period: String,
    timeFrame: Object,
  },
  computed: {
    getTitle() {
      const title = this.timeFrame.title || ""
      return title[0].toUpperCase() + title.slice(1)
    },
    currentCount() {
      return this.timeFrame.timeFrames[this.period].current
    },
    lastCount() {
      return this.timeFrame.timeFrames[this.period].previous
    },
    getPeriod() {
      switch (this.period) {
        case "daily":
          return "day"
      
        case "weekly":
          return "week"
        
        case "monthly":
          return "month"

        default:
          return ""
      }
    },
    getImageSrc() {
      return `images/${this.timeFrame.title}.svg`
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../assets/colors.scss';

.main-wrapper {
  margin: 10px 15px;
  width: 220px;
  height: 220px;
}

.three-dots-btn {
    display: inline-block;
    cursor: pointer;
    margin-bottom: 2px;
}

.three-dots-btn span {
    display: inline-block;
    width: 4px;
    height: 4px;
    background-color: white;
    border-radius: 50%;
    margin: 0 2px;
}

.first-class {
  border-radius: 10%;
  height: 150px;
  width: 220px;
  overflow: hidden;
}
.image {
  height: 55px;
  width: 55px;
  position: relative;
  left: 65px;
  bottom: 5px;
}

.second-class {
  background-color: $dark-blue;
  position: relative;
  bottom: 120px;
  border-radius: 10%;
  padding: 15px;
  width: 190px;
}

.second-class:hover {
  background-color: hsl(235, 46%, 30%);
  cursor: pointer;
}

.second-class-title {
  display:flex;
  justify-content: space-between;
  margin: 10px 5px;
}

.current {
  margin: 25px 0;
  display: flex;
}

.current span {
  font-size: 45px
}

.current p {
  margin-left: 5px;
  font-size: 18px;
}

.last {
  margin-bottom: 10px;
  color: $pale-blue;
  text-align: left;
}


.bg-job {
  background-color: $job;
}
.bg-fun {
  background-color:  $fun;
}
.bg-learning {
  background-color: $learning;
}
.bg-sport {
  background-color: $sport;
}
.bg-emails {
  background-color:  $emails;
}
.bg-health {
  background-color: $health;
}
</style>
