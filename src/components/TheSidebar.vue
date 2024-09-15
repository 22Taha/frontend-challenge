<template>
  <div class="warper">
    <div class="profile">
      <div class="avatar">
        <img src="../../public/images/avatar.png" style="width: 110%; height: 110%; object-fit: cover; object-position: center;" alt="User image">
      </div>
      <div class="profile-infos">
        <p class="sub-avatar">Report for</p>
        <p class="username">Stacey Castillo</p>
      </div>
    </div>
    <div class="menu">
      <div class="menu-item" :class="selectedMenuItemClass('daily')" @click="setTimeFrame('daily')">Daily</div>
      <div class="menu-item" :class="selectedMenuItemClass('weekly')" @click="setTimeFrame('weekly')">Weekly</div>
      <div class="menu-item" :class="selectedMenuItemClass('monthly')" @click="setTimeFrame('monthly')">Monthly</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheSidebar',
  props: {
    timeFrame: String,
  },
  data() {
    return {}
  },
  methods: {
    selectedMenuItemClass(item) {
      return {
        'selected-menu-item': this.timeFrame === item
      }
    },
    setTimeFrame(timeFrame) {
      this.$emit('changed-timeFrame', timeFrame)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/colors.scss';

.warper {
  background-color: $dark-blue;
  height: calc(100% - 20px);
  margin: 10px 20px 10px 0;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
}
.profile {
  padding: 30px;
  background-color: hsl(246, 80%, 60%);
  border-radius: 20px;
  text-align: left;
}

.avatar {
  border-radius: 50%;
  border: 2px solid #fff;
  width: 90px;
  height: 90px;
  overflow: hidden;
  text-align: left;
}

.sub-avatar {
  color: $pale-blue;
  margin: 20px 5px;
}

.username {
  font-size: 40px;
  margin: 0 0 30px 0;
}

.avatar img {
  width: 130px;
  height: 130px;
  position: relative;
  top: -3px;
  left: -5px;
}

.menu {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-grow: 1;
  justify-content: space-evenly;
}

.menu-item {
  color: $pale-blue;
}

.menu-item:hover {
  color: hsl(196, 100%, 86%);
  cursor: pointer;
}

.selected-menu-item {
  color: white;
}

</style>