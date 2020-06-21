<template>
  <div id="calendar-week" class="columns">
      <CalendarDay v-for="day in sharedState.seedData" :key="day.id" :day="day" />
  </div>
</template>

<script>
import store from '../store'
import CalendarDay from "./CalendarDay"

export default {
  name: "CalendarWeek",
  data() {
    return {
      sharedState: store.state
    };
  },
  components: {
    CalendarDay
  }
};
</script>

<style lang="scss" scoped>
  #calendar-week {
    margin-bottom: 50px;
    border-radius: 5%;
  .column {
    padding: 0 0 0 0;
  }
}

</style>
