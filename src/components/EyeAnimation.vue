<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'EyeAnimation',
  setup() {
    const isOpen = ref(false);

    function toggleEye() {
      setTimeout(() => {
        isOpen.value = !isOpen.value;
      }, isOpen.value ? 1000 : 1000); // open state pauses for 2.5 seconds, closed for 0.5 seconds
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


<style scoped>
.eye-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #222222 /* Semi-transparent black background */
}

.eye {
    width: 100px;
    height: 50px;
    background: #fff;
    position: relative;
    border-radius: 50%;
    border: solid 3px #000;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
}

.pupil {
    width: 50px;
    height: 50px; /* Height is 100% of the eye's vertical space */
    background: #000;
    border-radius: 50%;
}

.eyelid {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: #000;
    transition: bottom 1s ease;
}
</style>
