<script lang="ts" setup>
import { ref } from 'vue';

const props = defineProps<{
    videoSrc: any;
    image: any;
    title: string;
    description: string;
}>();

const showImage= ref(true);

const playVideo = (event: Event) => {
  const videoElement = event.target as HTMLVideoElement;
  if (videoElement) {
    videoElement.play();
  }
};

const pauseVideo = (event: Event) => {
  const videoElement = event.target as HTMLVideoElement;
  if (videoElement) {
    videoElement.pause();
    videoElement.currentTime = 0;
  }
};
</script>

<template>
    <div class="project">
        <div 
            class="video-container" 
            @click="$emit('imageClick')"
            @mouseenter="showImage = false" 
            @mouseleave="showImage = true" 
        >   
            <Transition name="fade">
                <img v-if="showImage" class="project-image" :src="image"/>
            </Transition>
            <Transition name="slow-fade">
            <video 
                v-if="!showImage"
                class="project-video"
                :src="videoSrc"
                loop 
                @mouseenter="playVideo" 
                @mouseleave="pauseVideo" 
                muted
            >
            </video>
            </Transition>
        </div>
        
        <div class="project-title">{{ title }}</div>
        <div class="project-description">{{ description }}</div>
    </div>
</template>