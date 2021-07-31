<template>
  <div class="dayDate">
    <div class="days">
      <span v-for="day in days" v-bind:key="day">{{ day }}</span>
    </div>
    <div class="nDays">
      <span
        @click="pullInfo(day)"
        v-for="day in dates.slice(0, nDays)"
        v-bind:key="day"
        >{{ day }}</span
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "dayDate",

  props: {
    firstDay: String,
    nDays: Number,
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
      console.log(day);
    },
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