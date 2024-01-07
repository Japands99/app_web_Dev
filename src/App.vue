<template>
  <header>
    <div class="d-flex justify-content-center align-items-center bg-success text-white" style="border-bottom: 3px solid #adadad;">
    </div>
  </header>
  <div class="container py-3" style="height: 100vh;">
    <div class="row">
      <div class="col-md-3" style="border-right: 3px solid #adadad;">


        <div @click="showFlexbox" class="card mt-3" :class="flexBox">
          <a class="text-decoration-none">
            <div class="card-body">
              <h5 class="card-title">Flexbox</h5>
              <p class="card-text">A CSS layout module.</p>
            </div>
          </a>
        </div>

        <div @click="showCountdownTimer" class="card mt-3" :class="countTimer">
          <a href="javascript: void(0)" class="text-decoration-none">
            <div class="card-body">
              <h5 class="card-title">Countdown Timer</h5>
              <p class="card-text">A countdown timer tool.</p>
            </div>
          </a>
        </div>

      </div>
      <Flexbox :showFlexboxComponent="showFlexboxComponent" />
      <CountdownTimer :showCountdownTimerComponent="showCountdownTimerComponent" />
    </div>
  </div>
</template>

<script>
import Flexbox from './components/Flexbox.vue';
import CountdownTimer from './components/CountdownTimer.vue';

export default {
  components: { Flexbox, CountdownTimer },
  data() {
    return {
      showFlexboxComponent: true,
      showCountdownTimerComponent: false,
      flexBox: 'active',
      countTimer: '',
    };
  },
  methods: {
    showFlexbox() {
      this.showFlexboxComponent = true;
      this.showCountdownTimerComponent = false;
      this.flexBox = 'active';
      this.countTimer = '';
    },
    showCountdownTimer() {
      this.showFlexboxComponent = false;
      this.showCountdownTimerComponent = true;
      this.flexBox = '';
      this.countTimer = 'active';
    },
  },
};
</script>

<style>
  div .active {
    background-color: #008fff;
    cursor: pointer;
  }

  div .active a {
    color: aliceblue;
  }

  div a {
    color: #2c3f50;
  }
</style>