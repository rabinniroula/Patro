<template>
  <div>
    <div class="monthInfo">
      <button @click="goBack">
        <img src="./assets/chevron-left.svg" alt="पछिल्लो महिना" />
      </button>
      <div class="month-year">
        <h1>{{ months[month - 1] }}</h1>
        <h1>{{ year }}</h1>
      </div>
      <button @click="goAhead">
        <img src="./assets/chevron-right.svg" alt="अघिल्लो महिना" />
      </button>
    </div>
    <dayDate
      :firstDay="fDay"
      :nDays="mLen"
      :today="today"
      :key="month"
    ></dayDate>

    <h3>
      Still in protype phase. More features coming soon... Made with ❤️ by
      <a
        href="https://github.com/rabinniroula"
        target="_blank"
        rel="noopener noreferrer"
        >Rabin Niroula</a
      >
    </h3>
  </div>
</template>

<script>
import { getTodayInBS, getBsMonthInfo } from "nepcalconv";
import dayDate from "./components/dayDate.vue";

export default {
  name: "App",
  components: {
    dayDate,
  },
  data() {
    return {
      fDay: 0,
      mLen: 0,
      today: 0,
      month: 0,
      year: 0,
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
    getTodaysInfo() {
      var Today = getTodayInBS();
      this.year = Today.year;
      this.month = Today.month;
      this.today = Today.day;
      this.monthChanged();
    },

    goBack() {
      this.month--;
      this.monthChanged();
      if (this.month < 1) {
        this.month = 12;
        this.year--;
      }
    },

    goAhead() {
      this.month++;
      this.monthChanged();
      if (this.month > 12) {
        this.month = 1;
        this.year++;
      }
    },

    monthChanged() {
      var monthInfo = getBsMonthInfo(this.year, this.month);
      this.fDay = monthInfo.firstDay;
      this.mLen = monthInfo.mLen;
      // console.log(this.fDay, this.mLen);
    },
  },

  beforeMount() {
    this.getTodaysInfo();
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
  text-align: center;
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

.monthInfo button:active {
  background: #926f69;
}

.month-year {
  height: 100px;
  width: 100px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.month-year h1 {
  margin: 0px;
}
</style>
