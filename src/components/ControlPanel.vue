<template>
  <div class="stopwatch__bottom-btns">
    <svg
      v-if="status"
      :class="['stopwatch__icon', 'pause', {active: status}]"
      width="10"
      height="20"
      viewBox="0 0 10 20"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      @click="$emit('pause')"
    >
      <rect x="7" width="3" height="20" fill="#9E9E9E"/>
      <rect width="3" height="20" fill="#9E9E9E"/>
    </svg>

    <svg
      v-else
      class="stopwatch__icon play"
      width="17"
      height="20"
      viewBox="0 0 17 20"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      @click="$emit('play')"
    >
      <path d="M0 20V0L17 10L0 20Z" fill="#9E9E9E"/>
    </svg>

    <svg
      :class="['stopwatch__icon', 'reset', {active: status}]"
      width="20"
      height="20"
      viewBox="0 0 20 20"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      @click="$emit('reset')"
    >
      <rect width="20" height="20" fill="#9E9E9E"/>
    </svg>

  </div>
</template>

<script>
export default {
  props: ['status'],
  name: 'ControlPanel'
}
</script>