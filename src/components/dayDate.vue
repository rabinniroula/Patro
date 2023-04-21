<template>
  <div class="dayDate">
    <div class="days">
      <span v-for="day in days" v-bind:key="day">{{ day }}</span>
    </div>
    <div class="nDays">
      <span
        @click="pullInfo(day)"
        v-for="day in dates"
        v-bind:key="day"
        :class="{
          weekend: (dates.indexOf(day) + 1) % 7 == 0 && day != '',
          thisDay: dates.indexOf(day) - firstDay + 1 == today,
        }"
      >
        {{ day }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "dayDate",

  props: {
    firstDay: Number,
    nDays: Number,
    today: Number,
  },

  data() {
    return {
      days: ["आइत", "सोम", "मंगल", "बुध", "बिही", "शुक्र", "शनि"],
      dates: [
        "१",
        "२",
        "३",
        "४",
        "५",
        "६",
        "७",
        "८",
        "९",
        "१०",
        "११",
        "१२",
        "१३",
        "१४",
        "१५",
        "१६",
        "१७",
        "१८",
        "१९",
        "२०",
        "२१",
        "२२",
        "२३",
        "२४",
        "२५",
        "२६",
        "२७",
        "२८",
        "२९",
        "३०",
        "३१",
        "३२",
      ],
    };
  },

  methods: {
    pullInfo(day) {
      console.log(this.dates.indexOf(day));
      //  console.log(this.firstDay+this.dates.indexOf(day), this.today)
    },
    formatView() {
      this.dates = this.dates.slice(0, this.nDays);
      for (let i = 0; i < this.firstDay; i++) {
        this.dates.unshift("");
      }
      try {
        let overflow = this.dates.slice(35, this.dates.length);
        for (let i in overflow) this.dates[i] = overflow[i];
        this.dates = this.dates.slice(0, 35);
      } catch {
        console.log("hello");
      }
    },
  },

  beforeMount() {
    this.formatView();
  },
};
</script>

<style scoped>
.dayDate {
  font-weight: 400;
  font-size: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.days,
.nDays {
  width: 650px;
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  border: 2px solid black;
  border-radius: 5px;
}

.days {
  margin-bottom: 10px;
}

span {
  height: 5rem;
  text-align: center;
  line-height: 5rem;
  cursor: pointer;
}
.days span {
  background: linear-gradient(to bottom right, #a6808c75, #a6808cb2);
}

.nDays span {
  background: linear-gradient(to bottom right, #70667775, #706677b2);
}

.nDays span:hover {
  background: linear-gradient(to top right, #70667775, #706677b2);
}
.nDays span:active {
  background: linear-gradient(to top right, #83748dc9, #504855);
}

.weekend {
  color: red;
}

.thisDay {
  color: blue;
}

@media only screen and (max-width: 600px) {
  .days,
  .nDays {
    width: 100%;
  }
  .dayDate {
    font-weight: 200;
    font-size: 1rem;
  }
  span {
    height: 50px;
    line-height: 50px;
  }
}
</style>
