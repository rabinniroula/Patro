<template>
  <div>
    <dayDate :firstDay="fDay" :nDays="31" :today="today"></dayDate>
  </div>
</template>

<script>
import { getTodayInBS } from "nepcalconv";
import dayDate from "./components/dayDate.vue";

export default {
  name: "App",
  components: {
    dayDate,
  },
  data() {
    return {
      fDay: 0,
      today: 0
    };
  },

  methods: {
    findDay(c, d) {
      for (d; d > 1; d--) {
        c--;
        if (c == -1) c = 6;
      }

      return c;
    },
  },

  beforeMount() {
    var Today = getTodayInBS()
    this.today = Today.day
    this.fDay = this.findDay(Today.weekday, Today.day)
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

body {
  border: 0px;
  margin: 0px;
  background: #d6cfcb;
}
</style>
