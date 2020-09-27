<template>
  <div class="app">
    <div class="app__wrapper">
      <Stopwatch v-for="index in stopwatchesCount" :key="index" />
      <div class="stopwatch stopwatch-add">
        <img
          class="add icon"
          src="./assets/icons/add.svg"
          alt="add"
          @click="stopwatchesCount++"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Stopwatch from './components/Stopwatch'

export default {
  name: 'App',
  components: {
    Stopwatch
  },
  data: () => ({
    stopwatchesCount: 0
  })
}
</script>