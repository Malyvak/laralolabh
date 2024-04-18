<script lang="ts" setup>
import { ref, watch, onBeforeMount } from 'vue';

interface StringSearchKeyMap {
  [key:string]: () => Promise<any>;
}

function importVideo(fileName: string) {
  return () => import(`@/assets/videos/showreel/${fileName}.mp4`);
}

const videoImports: StringSearchKeyMap = {
  '0': importVideo('001_ShowreelMiniCut-converted'),
  '1': importVideo('002_ShowreelMiniCut-converted'),
  '2': importVideo('003_ShowreelMiniCut-converted'),
  '3': importVideo('004_ShowreelMiniCut-converted'),
  '4': importVideo('005_ShowreelMiniCut-converted'),
  '5': importVideo('006_ShowreelMiniCut-converted'),
  '6': importVideo('007_ShowreelMiniCut-converted'),
  '7': importVideo('008_ShowreelMiniCut-converted'),
  '8': importVideo('009_ShowreelMiniCut-converted'),
  '9': importVideo('010_ShowreelMiniCut-converted'),
  '10': importVideo('011_ShowreelMiniCut-converted'),
  '11': importVideo('012_ShowreelMiniCut-converted'),
  '12': importVideo('013_ShowreelMiniCut-converted'),
  '13': importVideo('014_ShowreelMiniCut-converted'),
};



const currentVideoIndex = ref(0);
const currentVideo = ref('');

const videoPlayerKey = ref(Date.now());
const videoPlayer = ref<HTMLVideoElement | null>(null);
const isOverlayVisible = ref(false); 


const loadVideo = (index: number) => {
  const loader = videoImports[index.toString()];
  if (loader) {
    loader().then((module: { default: string; }) => {
      currentVideo.value = module.default;
      isOverlayVisible.value = true;
      setTimeout(() => {
        isOverlayVisible.value = false;
      }, 100);
    });
  }
};

onBeforeMount(() => {
  loadVideo(0);
});

const handleVideoEnd = () => {
    currentVideoIndex.value = (currentVideoIndex.value + 1) % Object.keys(videoImports).length;
    loadVideo(currentVideoIndex.value);
    videoPlayerKey.value = Date.now();
};

const videoLoaded = () => {
    videoPlayer.value?.play();
};

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
          <video
              class="showreel-video"
              :key="videoPlayerKey"
              ref="videoPlayer"
              autoplay
              muted
              playsinline
              @ended="handleVideoEnd"
              @loadedmetadata="videoLoaded"
              :class="{ 'fade-in': !isOverlayVisible }"
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