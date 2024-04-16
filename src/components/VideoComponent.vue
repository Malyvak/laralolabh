<script lang="ts" setup>
import { ref } from 'vue';
import playButton from '@/assets/icons/play-button-icon.png';

const props = defineProps<{
    videoSrc: any;
    image: any;
    title: string;
    description: string;
}>();

const showVideo= ref(false);
const videoElementRef = ref<HTMLVideoElement | null>(null);

const playVideo = () => {
    const videoElement = videoElementRef.value;
    if (videoElement) {
        videoElement.play();
    }
};

const pauseVideo = () => {
    const videoElement = videoElementRef.value;
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
                    ref="videoElementRef"
                    :src="videoSrc"
                    loop
                    muted
                >
                </video>
            </Transition>
            <div 
                class="play-button-wrapper"
                v-show="showVideo"
                @mouseenter="playVideo"
                @mouseleave="pauseVideo"
                >
                <img 
                    v-show="showVideo"
                    :src="playButton"
                    class="play-button"
                />
            </div>
        </div>
        
        <div class="project-title">{{ title }}</div>
        <div class="project-description">{{ description }}</div>
    </div>
</template>