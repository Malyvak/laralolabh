<script lang="ts" setup>
import logo from '@/assets/images/header-logo.png'
import { onMounted, onUnmounted, computed, ref } from 'vue';

const headerOpacity = computed(() => isScrollAtTop.value || isMouseOver.value);
const isScrollAtTop = ref(false);
const isMouseOver = ref(false);

onMounted(() => {
    window.addEventListener('mousemove', updateNavbarMouseVisibility);
    window.addEventListener('scroll', updateNavbarScrollVisibility); // Listen for scroll events
    updateNavbarScrollVisibility(); // Initial check in case the page is already scrolled
});

onUnmounted(() => {
    window.removeEventListener('mousemove', updateNavbarMouseVisibility);
    window.removeEventListener('scroll', updateNavbarScrollVisibility); // Remove scroll listener
});

function updateNavbarScrollVisibility() {
    const showNavbarScrollPosition = 50; // For scroll position

    if (window.scrollY <= showNavbarScrollPosition) {
        isScrollAtTop.value = true;
    } else {
        isScrollAtTop.value = false;
    }
}

function updateNavbarMouseVisibility(event?: MouseEvent) {
    const showNavbarMousePosition = 110; // For scroll position

    if (event && event.clientY <= showNavbarMousePosition) {
        isMouseOver.value = true;
    } else {
        isMouseOver.value = false;
    }
}

function scroll(id: string) {
    const element = document.getElementById(id);
    if (element) {
        element.scrollIntoView({behavior: 'smooth'});
    }
}
</script>


<template>
    <Transition name="fade">
        <header v-if="headerOpacity" class="header">
            <nav class="navbar">
                <img class="brand" :src="logo"/>
                <div class="nav-links">
                    <a @click="() => scroll('showreel')" class="nav-link">HOME</a>
                    <a @click="() => scroll('editing')" class="nav-link">EDITING WORK</a>
                    <a @click="() => scroll('professional-information')" class="nav-link">PROFESSIONAL INFORMATION</a>
                    <a @click="() => scroll('about-me')" class="nav-link">ABOUT ME</a>
                    <a @click="() => scroll('contact-me')" class="nav-link contact">CONTACT ME</a>
                </div>
            </nav>
        </header>
    </Transition>
</template>