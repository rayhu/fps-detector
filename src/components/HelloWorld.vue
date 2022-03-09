<script setup>
defineProps({
  msg: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      <span>
        <button :disabled="running" @click="startDetect">start</button>
      </span>
      <span>
        <button :disabled="!stoppable" @click="stopDetect">stop</button>
      </span>
      <p id="results">Results:</p>
      <canvas id="canvas" width="300" height="300"></canvas>
      <h5>
        Based on
        <a target="_blank" href="https://vitejs.dev/">Vite</a> +
        <a target="_blank" href="https://vuejs.org/">Vue 3</a>.
      </h5>
    </h3>
  </div>
</template>

<script>
import $ from "jquery";

export default {
  data() {
    return {
      running: false,
      fps: 0,
      frameCount: 0,
      stoppable: false,
    };
  },
  mounted() {},
  methods: {
    startDetect() {
      this.running = true;
      var frameCount = 0;
      var $results = $("#results");
      var fpsInterval, startTime, now, then, elapsed;
      
      // uplimit will be 240 fps
      startAnimating.bind(this)(240);

      function startAnimating(fps) {
        fpsInterval = 1000 / fps;
        then = Date.now();
        startTime = then;
        console.log(startTime);
        animate.bind(this)();
      }
      function animate() {
        // stop
        if (!this.running) {
          return;
        }

        // request another frame

        requestAnimationFrame(animate.bind(this));

        // calc elapsed time since last loop

        now = Date.now();
        elapsed = now - then;

        // if enough time has elapsed, draw the next frame

        if (elapsed > fpsInterval) {
          // Get ready for next frame by setting then=now, but...
          // Also, adjust for fpsInterval not being multiple of 16.67
          then = now - (elapsed % fpsInterval);

          // draw stuff here

          // TESTING...Report #seconds since start and achieved fps.
          var sinceStart = now - startTime;
          var currentFps =
            Math.round((1000 / (sinceStart / ++frameCount)) * 100) / 100;
          $results.text(
            "Elapsed time= " +
              Math.round((sinceStart / 1000) * 100) / 100 +
              " secs @ " +
              currentFps +
              " fps."
          );
        }
      }
      setTimeout(() => {
        this.stoppable = true;
      }, 5000);
    },
    stopDetect() {
      this.running = false;
    },
  },
};
</script>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
