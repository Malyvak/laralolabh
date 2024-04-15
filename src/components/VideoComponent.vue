<script lang="ts" setup>
import { ref } from 'vue';

const props = defineProps<{
    videoSrc: any;
    image: any;
    title: string;
    description: string;
}>();

const showVideo= ref(false);

const playVideo = (event: Event) => {
    const videoElement = event.target as HTMLVideoElement;
    if (videoElement) {
        videoElement.play();
    }
};

const pauseVideo = (event: Event) => {
    const videoElement = event.target as HTMLVideoElement;
    if (videoElement) {
        setTimeout(() => {
            videoElement.pause();
            videoElement.currentTime = 0;
        }, 1000);
    }
};
</script>

<template>
    <div class="video-component">
        <div 
            class="video-container" 
            @click="$emit('imageClick')"
            @mouseenter="showVideo = true" 
            @mouseleave="showVideo = false" 
        >   
            <img class="project-image" :src="image"/>
            <Transition name="slow-fade">
                <video 
                    v-if="showVideo"
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