<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import playButton from '@/assets/icons/play-button-icon.png';

const props = defineProps<{
    image: string;
    title: string;
    description: string;
}>();

const imageSrc = ref('');

onMounted(() => {
    loadImage();
});

const loadImage = async () => {
  const module = await import(`@/assets/images/${props.image}.png`);
  imageSrc.value = module.default;
};
</script>

<template>
    <div class="phone-video-component">
        <div 
            class="video-container" 
            @click="$emit('imageClick')"
        >   
            <img class="project-image" :src="imageSrc"/>
            <div 
                class="play-button-wrapper">
                <img class="play-button" :src="playButton"/>
            </div>
        </div>
        
        <div class="project-title">{{ title }}</div>
        <div class="project-description">{{ description }}</div>
    </div>
</template>