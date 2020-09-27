<template>
  <div class="stopwatch">
    <div :class="['stopwatch__top', {active: status}]">{{getTime}}</div>
    <div class="stopwatch__bottom">
      <ControlPanel
        :status="status"
        @play="play"
        @pause="pause"
        @reset="reset"
      />
    </div>
  </div>
</template>

<script>
import ControlPanel from './ControlPanel'

export default {
  name: 'Stopwatch',
  components: {
    ControlPanel
  },
  data: () => ({
    time: {
      seconds: 0,
      minutes: 0,
      hours: 0
    },
    timerId: null,
    status: false
  }),
  methods: {
    play() {
      this.status = true
      
      this.timerId = setInterval(() => {
        this.time.seconds++

        if(this.time.seconds === 60) {
          this.time.minutes++
          this.time.seconds = 1
        }

        if(this.time.minutes === 60) {
          this.time.hours++
          this.time.minutes = 0
        }
      }, 1000)
    },
    pause() {
      this.status = false
      clearInterval(this.timerId)
    },
    reset() {
      this.pause()
      this.time = {
        seconds: 0,
        minutes: 0,
        hours: 0
      }
    }
  },
  computed: {
    getTime() {
      const { hours, minutes, seconds } = this.time
      return (hours > 0 ? hours + ':' : '') + (minutes > 0 || hours > 0 ? minutes + ':' : '') + seconds
    }
  }
}
</script>