<script lang="ts" setup>
import { ref } from 'vue';

// const FILE_ID = '1C5zkkZOWj08mc7-hGH2LG5d4Mml5lI19';
// const videoURL = ref(`https://drive.google.com/uc?export=download&id=${FILE_ID}`);

</script>

<template>
    <section class="showreel">
        <div class="showreel-container">
            <!-- <video v-if="videoURL" class="showreel-video" autoplay loop muted>
                <source :src="videoURL" type="video/mp4">
                Your browser does not support the video tag.
            </video>  -->
            <video class="showreel-video" autoplay loop muted>
                <source src="@/assets/videos/Video10_Frog.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>
        <div class="showreel-subtext-container">
            <div class="showreel-subtext">
                <span class="bold">MY SHOWREEL</span> - A SERIES OF SNIPPETS SELECTED FROM SOME OF MY ALL-TIME FAVOURITE EDITS
            </div>
        </div>
    </section>
</template>