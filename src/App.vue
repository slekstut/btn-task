<template>
  <div id="app">
    <button class="button" @click="toggleClass">
      I will unlock Second Button on click
    </button>
    <button
      class="button"
      :class="{ 'button--locked': isLocked }"
      @click="countdownClick"
    >
      <span v-if="!isLocked"
        >I will unlock Third Button after {{ countdown }} clicks</span
      >
      <span v-else>Oh no! I am locked :(</span>
    </button>
    <button class="button" :class="{ 'button--locked': thirdBtnLocked}">
      <span v-if="thirdBtnLocked">Oh no! I am locked :(</span>
      <span v-else>Yay I'm free! :)</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      isLocked: true,
      countdown: 5,
      thirdBtnLocked: true
    };
  },
  methods: {
    toggleClass() {
      console.log("toggleClass activated!");
      this.isLocked = !this.isLocked;
      console.log(this.isLocked);
    },
    countdownClick() {
      if (this.counddown !== 0) this.countdown -= 1;
      console.log(this.countdown);
      if (this.countdown === 0) this.thirdBtnLocked = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.button {
  background-color: #fff263;
  border: 2px solid #c49000;
  border-radius: 8px;
  box-shadow: 2px 2px 5px #888888;
  cursor: pointer;
  display: block;
  padding: 8px 16px;
  margin: 4px;
  transform: translate(-2px, -2px);
  transition: transform 0.1s, box-shadow 0.1s, background-color 0.1s;
  width: 300px;
}

.button:active {
  transform: translate(0, 0);
  box-shadow: 0 0 #888888;
}

.button--locked {
  background-color: #efefef;
  border-color: #8d8d8d;
  cursor: not-allowed;
  opacity: 1;
  transform: translate(0, 0);
  box-shadow: 0 0 #888888;
}
</style>
