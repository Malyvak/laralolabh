<script lang="ts" setup>

const props = defineProps<{
    videoId: string;
    showModal: boolean;
}>();

const emit = defineEmits(['close']);

const close = () => {
    emit('close');
};
</script>

<template>
    <Transition name="fade">
        <div v-if="showModal" class="modal-overlay" @click.self="close">
            <div class="modal-content">
                <div class="button-container">
                    <svg 
                        @click="close"
                        class="close-button"
                        xmlns="http://www.w3.org/2000/svg" 
                        viewBox="0 0 24 24">
                        <path fill="#fff" d="M19 6.41L17.59 5L12 10.59L6.41 5L5 6.41L10.59 12L5 17.59L6.41 19L12 13.41L17.59 19L19 17.59L13.41 12z" />
                    </svg>
                </div>
                <iframe 
                    class="youtube-video"
                    width="560" 
                    height="315" 
                    :src="`https://www.youtube.com/embed/${videoId}`" 
                    title="YouTube video player" 
                    frameborder="0" 
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
                    referrerpolicy="strict-origin-when-cross-origin" 
                    allowfullscreen></iframe>
            </div>
        </div>
    </Transition>
</template>

