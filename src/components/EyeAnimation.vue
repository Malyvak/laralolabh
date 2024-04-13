<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'EyeAnimation',
  setup() {
    const isOpen = ref(true);

    function toggleEye() {
      setTimeout(() => {
        isOpen.value = !isOpen.value;
      }, isOpen.value ? 1500 : 500); // open state pauses for 2.5 seconds, closed for 0.5 seconds
    }

    setInterval(toggleEye, 2000); // Adjusts the interval for the complete open-close cycle

    return { isOpen }
  }
});
</script>


<template>
  <div class="eye-wrapper">
    <div class="eye">
      <div class="pupil"></div>
      <div class="eyelid" :style="{ bottom: isOpen ? '100%' : '0%' }"></div>
    </div>
  </div>
</template>

