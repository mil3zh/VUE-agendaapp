<template>
  <div id="calendar-entry" class="mycard">
      <p>New Event:</p>
      <input type="text" placeholder="New Event" v-model="inputEntry" required />
      <p class="calendar-entry-day">
        Date:
        <span class="bold">{{ titleOfActiveDay }}</span>
      </p>
      <a class="button is-primary is-small is-outlined" @click="submitEvent(inputEntry)">Submit</a>
    <p style="color: red; font-size: 13px" v-if="error">You must type something first!</p>
  </div>
</template>

<script>
import  store  from "../store";

export default {
  name: "CalendarEntry",
  data() {
    return {
      inputEntry: ""
    };
  },
  computed: {
    titleOfActiveDay() {
      return store.getActiveDay().fullTitle;
    }
  },
  methods: {
    submitEvent(eventDetails) {
      if (eventDetails === "") return (this.error = true);
      store.submitEvent(eventDetails);
      this.inputEntry = "";
      this.error = false;
    }
  }
};
</script>

<style lang="scss" scoped>
.mycard{
  display: block;
  width: fit-content;
  height: auto;
  background-color: white;
  position: relative;
  border: solid grey 0.5px;
  border-radius: 5%;
  padding: 5%;
  bottom: 30%;
}

p{
  text-align: left;
}
</style>