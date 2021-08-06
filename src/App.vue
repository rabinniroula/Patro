<template>
  <div>
    <div class="monthInfo">
      <button>
        <img src="./assets/chevron-left.svg" alt="पछिल्लो महिना" />
      </button>
      <h1>{{ months[month - 1] }}</h1>
      <button>
        <img src="./assets/chevron-right.svg" alt="अघिल्लो महिना" />
      </button>
    </div>
    <dayDate :firstDay="fDay" :nDays="32" :today="today"></dayDate>

    <h3>Still in protype phase. More features coming soon. Made with ❤️ by <a href="https://github.com/rabinniroula" target="_blank" rel="noopener noreferrer">Rabin Niroula</a> </h3>
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
      today: 0,
      month: "",
      months: [
        "बैशाख",
        "जेष्ठ",
        "असार",
        "श्रावण",
        "भाद्र",
        "आश्विन",
        "कार्तिक",
        "मंसिर",
        "पुष",
        "माघ",
        "फाल्गुण",
        "चैत्र",
      ],
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
    var Today = getTodayInBS();
    this.month = Today.month;
    this.today = Today.day;
    this.fDay = this.findDay(Today.weekday, Today.day);
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

.monthInfo {
  display: flex;
  /* margin: 5px; */
  justify-content: center;
  align-items: center;
}

.monthInfo button {
  margin-bottom: 10px;
  margin-top: 10px;
  margin-left: 40px;
  margin-right: 40px;
  width: 30px;
  height: 30px;
  border: 2px solid black;
  border-radius: 50%;
  cursor: pointer;
  background: #dda89f;
}

.monthInfo button:active{
  background: #926f69;
}
</style>
