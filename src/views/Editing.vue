<script lang="ts" setup>
import { ref } from 'vue';
import VideoComponent from '@/components/VideoComponent.vue';
import VideoModal from '@/components/VideoModal.vue';
import projectsData from '@/data/videos.json';

import image1 from '@/assets/images/Image1_GoFStill.png';
import image2 from '@/assets/images/Image2_BlondedLIAG.png';
import image3 from '@/assets/images/Image3_CampCourage.png';
import image4 from '@/assets/images/Image4_VoL.png';
import image5 from '@/assets/images/Image5_WBGS1.png';
import image6 from '@/assets/images/Image6_SixPivot.png';
import image7 from '@/assets/images/Image7_KyFurneaux.png';
import image8 from '@/assets/images/Image8_WBGS2.png';
import image9 from '@/assets/images/Image9_BlondedOC.png';
import image10 from '@/assets/images/Image10_Frog.png';

import video1 from '@/assets/videos/001-short-converted.mp4';
import video2 from '@/assets/videos/002-short-converted.mp4';
import video3 from '@/assets/videos/003-short-converted.mp4';
import video4 from '@/assets/videos/004-short-converted.mp4';
import video5 from '@/assets/videos/005-short-converted.mp4';
import video6 from '@/assets/videos/006-short-converted.mp4';
import video7 from '@/assets/videos/007-short-converted.mp4';
import video8 from '@/assets/videos/008-short-converted.mp4';
import video9 from '@/assets/videos/009-short-converted.mp4';
import video10 from '@/assets/videos/010-short-converted.mp4';

interface StringSearchKeyMap {
    [key: string]: any;
}

const imageMap: StringSearchKeyMap = {
  image1: image1,
  image2: image2,
  image3: image3,
  image4: image4, 
  image5: image5,
  image6: image6,
  image7: image7,
  image8: image8,
  image9: image9, 
  image10: image10,
};

const videoMap: StringSearchKeyMap = {
  image1: video1,
  image2: video2,
  image3: video3,
  image4: video4, 
  image5: video5,
  image6: video6,
  image7: video7,
  image8: video8,
  image9: video9, 
  image10: video10,
};

const showModal = ref(false);
const currentVideoId = ref('');

const openModal = (videoId: string) => {
  currentVideoId.value = videoId;
  showModal.value = true;
};

const closeModal = () => {
  showModal.value = false;
};

</script>

<template>
    <section id="editing" class="editing">
        <h1 class="title">EDITING WORK</h1>

        <div class="projects">
            <div class="projects">
            <VideoComponent
                v-for="project in projectsData"
                :key="project.title"
                :videoSrc="videoMap[project.image]"
                :image="imageMap[project.image]"
                :title="project.title"
                :description="project.description"
                @click.native="openModal(project.link)"
            />
            </div>
            <VideoModal
                :showModal="showModal"
                :videoId="currentVideoId"
                @close="closeModal"
            />
        </div>
    </section>
</template>