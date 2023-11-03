<script lang="ts" setup>
const props = defineProps<{
    image: string;
    title: string;
    description: string;
}>();


</script>

<template>
    <div class="project">
        <img :src=image>
        <div class="project-title">{{ title }}</div>
        <div class="project-description">{{ description }}</div>
    </div>
</template>