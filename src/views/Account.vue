<template>
  <div class="row">
    <div class="col-left">
      <h1>My Daily Tasks</h1>
    <p>Hit Enter to add your own personal tasks to the list<br> and mark them as complete when you're done!</p>
      <TaskList />
    </div>
    <div class="col-right">
      <h1>My Profile</h1>
      <img :src="$auth.user.picture" />
      <h2>{{ $auth.user.name }}</h2>
      <h4>{{ $auth.user.email }}</h4>
    </div>  
    <div class="calendar-container">
      <h1>My Weekly Events</h1>
      <CalendarWeek />
      <CalendarEntry />
    </div>
    <!--<div>
      <pre>{{ JSON.stringify($auth.user, null, 2) }}</pre>
    </div>-->
  </div>
</template>

<script>
import CalendarWeek from "../components/CalendarWeek";
import CalendarEntry from "../components/CalendarEntry";
import TaskList from "../components/TaskList";

export default {
  name: "account",
  components: {
    CalendarWeek,
    CalendarEntry,
    TaskList
  }
};
</script>

<style lang="scss" scoped>
.row {
  
  margin-top: 0;
  margin-bottom: 0;
  margin-left: 22%;
  margin-right: 22%;
}

.col-left {
  width: 65%;
  float: left;
  padding-right: 2%;
}

.col-right {
  width: 35%;
  float: right;

  
}

h1{
  font-weight: 800;
  color: rgb(4, 4, 39);
  font-size: 2em;
  text-align: left;
  padding: 1%;
  margin: 0 3% 3% 0;
}

p{
  text-align: left;
  margin: 0 3% 3% 0;
}

img {
  width: 200px;
  align-self: center;
  padding: 1%;
}

.calendar-container{
  margin: 1%;
  flex: 1;

}
.buttons {
  margin-bottom: 10px;
}
</style>