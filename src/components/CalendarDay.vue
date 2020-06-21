<template>
  <div class="day column" @click="setActiveDay(day.id)">
    <div class="day-banner has-text-centered">{{ day.abbvTitle }}</div>
    <div class="day-details">
      <CalendarEvent v-for="(event, index) in day.events" :key="index" :event="event" :day="day" />
    </div>
  </div>
</template>

<script>
import store from "../store";
import CalendarEvent from "./CalendarEvent.vue";
export default {
  name: "CalendarDay",
  props: ["day"],
  methods: {
    setActiveDay(dayId) {
      store.setActiveDay(dayId);
    }
  },
  components: {
    CalendarEvent
  }
};
</script>


<style lang="scss" scoped>
.day {
  background-color: white;
  color: #fff;
  border-left: 1px solid #8f8f8f;
  font-size: 12px;
  cursor: pointer;
  &:hover {
    background: rgb(196, 196, 245);
  }
  .day-banner {
    background-color: #e9ca3f;
    color: rgb(4, 4, 39);
    padding: 10px;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-size: 12px;
    font-weight: 600;
  }
  .day-details {
    padding: 10px;
  }&:first-child{
    border-left:none;
  }
  
}
</style>