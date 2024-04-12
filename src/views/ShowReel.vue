<script lang="ts" setup>
import { ref, watch, onMounted } from 'vue';

const videoImports: VideoImports = {
  '0': () => import('@/assets/videos/showreel/001_ShowreelMiniCut-converted.mp4'),
  '1': () => import('@/assets/videos/showreel/002_ShowreelMiniCut-converted.mp4'),
  '2': () => import('@/assets/videos/showreel/003_ShowreelMiniCut-converted.mp4'),
  '3': () => import('@/assets/videos/showreel/004_ShowreelMiniCut-converted.mp4'),
  '4': () => import('@/assets/videos/showreel/005_ShowreelMiniCut-converted.mp4'),
  '5': () => import('@/assets/videos/showreel/006_ShowreelMiniCut-converted.mp4'),
  '6': () => import('@/assets/videos/showreel/007_ShowreelMiniCut-converted.mp4'),
  '7': () => import('@/assets/videos/showreel/008_ShowreelMiniCut-converted.mp4'),
  '8': () => import('@/assets/videos/showreel/009_ShowreelMiniCut-converted.mp4'),
  '9': () => import('@/assets/videos/showreel/010_ShowreelMiniCut-converted.mp4'),
  '10': () => import('@/assets/videos/showreel/011_ShowreelMiniCut-converted.mp4'),
  '11': () => import('@/assets/videos/showreel/012_ShowreelMiniCut-converted.mp4'),
  '12': () => import('@/assets/videos/showreel/013_ShowreelMiniCut-converted.mp4'),
  '13': () => import('@/assets/videos/showreel/014_ShowreelMiniCut-converted.mp4')
};

interface VideoImports {
  [key:string]: any;
}
type VideoSource = string;
const videoSources: VideoSource[] = [];

const currentVideoIndex = ref(0);
const currentVideo = ref('');

const videoPlayerKey = ref(Date.now());
const videoPlayer = ref<HTMLVideoElement | null>(null);
const isOverlayVisible = ref(false); 


const loadVideo = (index: number) => {
  const loader = videoImports[index.toString()];
  if (loader) {
    loader().then((module: { default: string; }) => {
      videoSources[index] = module.default;
      currentVideo.value = module.default;
    });
  }
};

// Initial load for the first video
onMounted(() => {
  loadVideo(0);
});

const handleVideoEnd = () => {
  isOverlayVisible.value = true; // Show overlay (fade to black)
  setTimeout(() => {
    currentVideoIndex.value = (currentVideoIndex.value + 1) % Object.keys(videoImports).length;
    loadVideo(currentVideoIndex.value);
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