<template>
  <div class="container d-flex justify-content-center">
    <div class="row">
      <div class="group-1" :class="{ christmasGreen: group1Active }"></div>
      <div class="group-2" :class="{ christmasRed: group2Active }"></div>
      <div class="group-1" :class="{ christmasGreen: group1Active }"></div>
      <div class="group-2" :class="{ christmasRed: group2Active }"></div>
      <div class="group-1" :class="{ christmasGreen: group1Active }"></div>
      <div class="group-2" :class="{ christmasRed: group2Active }"></div>
      <div class="group-1" :class="{ christmasGreen: group1Active }"></div>
      <button
        class="btn btn-primary"
        style="margin-left: 1.5em;"
        @click="startLightShow"
      >
        Start Light Show
      </button>
      <input type="text" v-model="timerIntensity" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timerIntensity: 2000,
      timerStarted: false,
      group1Active: true,
      group2Active: false
    };
  },
  methods: {
    startLightShow() {
      this.timerStarted = !this.timerStarted;
      let timer = setInterval(() => {
        if (!this.timerStarted) {
          clearInterval(timer);
          return;
        }
        this.testNum++;
        this.group1Active = !this.group1Active;
        this.group2Active = !this.group2Active;
      }, this.timerIntensity);
    }
  }
};
</script>

<style>
.group-1,
.group-2 {
  height: 25px;
  width: 25px;
  background-color: #bbb;
  border-radius: 50%;
}

.christmasGreen {
  background-color: #4caf50;
}
.christmasRed {
  background-color: #ff3333;
}

.container {
  min-height: 100%; /* Fallback for browsers do NOT support vh unit */
  min-height: 100vh; /* These two lines are counted as one :-)       */

  display: flex;
  align-items: center;
}
</style>

