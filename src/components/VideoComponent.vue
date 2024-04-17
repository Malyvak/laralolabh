<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import playButton from '@/assets/icons/play-button-icon.png';

const props = defineProps<{
    video: string;
    image: string;
    title: string;
    description: string;
}>();

const imageSrc = ref('');
const videoSrc = ref('');
const showVideo= ref(false);
const videoElementRef = ref<HTMLVideoElement | null>(null);


onMounted(() => {
    loadImage();
    loadVideo();
});

const loadImage = async () => {
  const module = await import(`@/assets/images/${props.image}.png`);
  imageSrc.value = module.default;
};

const loadVideo = async () => {
  const module = await import(`@/assets/videos/${props.video}.mp4`);
  videoSrc.value = module.default; 
};

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
            <img class="project-image" :src="imageSrc"/>
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