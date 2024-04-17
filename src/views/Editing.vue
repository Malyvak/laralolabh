<script lang="ts" setup>
import { ref } from 'vue';
import VideoComponent from '@/components/VideoComponent.vue';
import PhoneVideoComponent from '@/components/PhoneVideoComponent.vue';
import VideoModal from '@/components/VideoModal.vue';
import projectsData from '@/data/videos.json';


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
          <div class="video-components">
          <VideoComponent
              v-for="project in projectsData"
              :key="project.title"
              :video="project.video"
              :image="project.image"
              :title="project.title"
              :description="project.description"
              @click.native="openModal(project.link)"
          />
          <PhoneVideoComponent
            v-for="project in projectsData"
              :key="project.title"
              :image="project.image"
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
    </section>
</template>