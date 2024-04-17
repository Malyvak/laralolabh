<script lang="ts" setup>
import { ref} from 'vue';
import ShowReel from '@/views/ShowReel.vue';
import Editing from '@/views/Editing.vue';
import ProfessionalInformation from './views/ProfessionalInformation.vue';
import AboutMe from './views/AboutMe.vue';
import ContactMe from './views/ContactMe.vue';
import NavBar from './components/NavBar.vue';
import videoSrc from '@/assets/videos/showreel/014_ShowreelMiniCut-converted.mp4';

const isVideoEnded = ref(false);

function handleVideoEnd() {
    isVideoEnded.value = true;
}

</script>

<template>
    <transition name="site-fade">
        <div v-if="!isVideoEnded" class="intro-video-container">
            <video autoplay muted playsinline @ended="handleVideoEnd" class="intro-centered-video">
                <source :src="videoSrc" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>

        <div v-else>
            <NavBar/>
            <ShowReel/>
            <Editing/>
            <ProfessionalInformation/>
            <AboutMe/>
            <ContactMe/>
        </div>
    </transition>
</template>


