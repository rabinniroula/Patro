<template>
  <div>
    <dayDate :firstDay="आइत" :nDays="31"></dayDate>
  </div>
</template>

<script>
import dayDate from "./components/dayDate.vue";

export default {
  name: "App",
  components: {
    dayDate,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Mukta&display=swap");

#app {
  font-family: "Mukta", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

body{
  border: 0px;
  margin: 0px;
  background: #D6CFCB;
}
</style>
