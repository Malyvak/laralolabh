<script lang="ts" setup>
import { ref, watch } from 'vue';

import video1 from '@/assets/videos/showreel/001_ShowreelMiniCut.mp4';
import video2 from '@/assets/videos/showreel/002_ShowreelMiniCut.mp4';
import video3 from '@/assets/videos/showreel/003_ShowreelMiniCut.mp4';
import video4 from '@/assets/videos/showreel/004_ShowreelMiniCut.mp4';
import video5 from '@/assets/videos/showreel/005_ShowreelMiniCut.mp4';
import video6 from '@/assets/videos/showreel/006_ShowreelMiniCut.mp4';
import video7 from '@/assets/videos/showreel/007_ShowreelMiniCut.mp4';
import video8 from '@/assets/videos/showreel/008_ShowreelMiniCut.mp4';
import video9 from '@/assets/videos/showreel/009_ShowreelMiniCut.mp4';
import video10 from '@/assets/videos/showreel/010_ShowreelMiniCut.mp4';
import video11 from '@/assets/videos/showreel/011_ShowreelMiniCut.mp4';
import video12 from '@/assets/videos/showreel/012_ShowreelMiniCut.mp4';
import video13 from '@/assets/videos/showreel/013_ShowreelMiniCut.mp4';
import video14 from '@/assets/videos/showreel/014_ShowreelMiniCut.mp4';

type VideoSource = string;

const videoSources: VideoSource[] = [
  video1, video2, video3, video4, video5, video6, video7, video8, video9,
  video10, video11, video12, video13, video14
];


const currentVideoIndex = ref(0);
const currentVideo = ref(videoSources[0]);
const videoPlayerKey = ref(Date.now());
const videoPlayer = ref<HTMLVideoElement | null>(null);
const isOverlayVisible = ref(false); // Controls the visibility of the overlay

const handleVideoEnd = () => {
  isOverlayVisible.value = true; // Show overlay (fade to black)
  setTimeout(() => {
    currentVideoIndex.value = (currentVideoIndex.value + 1) % videoSources.length;
    currentVideo.value = videoSources[currentVideoIndex.value];
    videoPlayerKey.value = Date.now(); // Update key to force re-render of video element
  }, 500); // Delay to allow overlay to become fully visible
};

const videoLoaded = () => {
  setTimeout(() => {
    isOverlayVisible.value = false; // Hide overlay (fade in video)
    videoPlayer.value?.play();
  }, 500); // Delay to allow a smooth fade-in effect
};

// Watch the currentVideo to load the new source whenever it changes
watch(currentVideo, () => {
  if (videoPlayer.value) {
    videoPlayer.value.load();
  }
});
</script>


<template>
    <section id="showreel" class="showreel">
      <div class="showreel-content">
        <div class="showreel-container">
          <div
            class="overlay"
            :class="{ 'is-visible': isOverlayVisible }"
          ></div>
          <video
              class="showreel-video"
              :key="videoPlayerKey"
              ref="videoPlayer"
              autoplay
              muted
              @ended="handleVideoEnd"
              @loadedmetadata="videoLoaded"
          >
              <source :src="currentVideo" type="video/mp4" />
              Your browser does not support the video tag.
          </video>
        </div>
      </div>
      <div class="showreel-subtext-container">
          <div class="showreel-subtext">
              <span class="bold">MY SHOWREEL</span> - A SERIES OF SNIPPETS SELECTED FROM SOME OF MY ALL-TIME FAVOURITE EDITS
          </div>
      </div>
    </section>
</template>