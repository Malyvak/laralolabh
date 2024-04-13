<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import EyeAnimation from './components/EyeAnimation.vue';
import ShowReel from '@/views/ShowReel.vue';
import Editing from '@/views/Editing.vue';
import ProfessionalInformation from './views/ProfessionalInformation.vue';
import AboutMe from './views/AboutMe.vue';
import ContactMe from './views/ContactMe.vue';
import NavBar from './components/NavBar.vue';

const isLoaded = ref(false);

import image1 from '@/assets/images/header-logo.png';
import image2 from '@/assets/images/Image1_GoFStill.png';
import image3 from '@/assets/images/Image2_BlondedLIAG.png';
import image4 from '@/assets/images/Image3_CampCourage.png';
import image5 from '@/assets/images/Image4_VoL.png';
import image6 from '@/assets/images/Image5_WBGS1.png';
import image7 from '@/assets/images/Image6_SixPivot.png';
import image8 from '@/assets/images/Image7_KyFurneaux.png';
import image9 from '@/assets/images/Image8_WBGS2.png';
import image10 from '@/assets/images/Image9_BlondedOC.png';
import image11 from '@/assets/images/Image10_Frog.png';
import image12 from '@/assets/images/EyePainting.jpg';
import image13 from '@/assets/images/QuoteCircle.png';


const assetUrls = [image1, image2, image3, image4, 
    image5, image6, image7, image8, image9, image10, 
    image11, image12, image13
]; // Add all image URLs here

function loadAssets() {
    let loadedCount = 0;
    const totalCount = assetUrls.length;

    assetUrls.forEach(url => {
        const img = new Image();
        img.src = url;
        img.onload = checkAssetLoaded;
    });

    function checkAssetLoaded() {
        loadedCount++;
        if (loadedCount === totalCount) {
            isLoaded.value = true;
        }
    };
}

onMounted(loadAssets);
</script>

<template>
    <transition name="site-fade">
        <div v-if="!isLoaded">
            <EyeAnimation/>
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
