<script lang="ts" setup>
import logo from '@/assets/images/header-logo.png'
import { onMounted, onUnmounted, computed, ref, toValue } from 'vue';

const headerOpacity = computed(() => isScrollAtTop.value || isMouseOver.value);
const isScrollAtTop = ref(false);
const isMouseOver = ref(false);
const isMenuVisible = ref(false);

onMounted(() => {
    window.addEventListener('mousemove', updateNavbarMouseVisibility);
    window.addEventListener('scroll', updateNavbarScrollVisibility); 
    updateNavbarScrollVisibility(); 
});

onUnmounted(() => {
    window.removeEventListener('mousemove', updateNavbarMouseVisibility);
    window.removeEventListener('scroll', updateNavbarScrollVisibility); 
});

function updateNavbarScrollVisibility() {
    const showNavbarScrollPosition = 50; 

    if (window.scrollY <= showNavbarScrollPosition) {
        isScrollAtTop.value = true;
    } else {
        isScrollAtTop.value = false;
    }
}

function updateNavbarMouseVisibility(event?: MouseEvent) {
    const showNavbarMousePosition = 110; 

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

function toggleMenu() {
    isMenuVisible.value = !isMenuVisible.value;
}
</script>


<template>
    <Transition name="fade">
        <header v-if="headerOpacity" class="header">
            <nav class="navbar">
                <img @click="toggleMenu" class="brand" :src="logo"/>
                <div class="nav-links">
                    <a @click="() => scroll('showreel')" class="nav-link">HOME</a>
                    <a @click="() => scroll('editing')" class="nav-link">EDITING WORK</a>
                    <a @click="() => scroll('professional-information')" class="nav-link">PROFESSIONAL INFORMATION</a>
                    <a @click="() => scroll('about-me')" class="nav-link">ABOUT ME</a>
                    <a @click="() => scroll('contact-me')" class="nav-link contact">CONTACT ME</a>
                </div>
            </nav>
            <nav class="navbar-tablet">
                <img @click="toggleMenu" class="brand" :src="logo"/>
                <Transition name="slide-out">
                    <div v-if="isMenuVisible" class="nav-links">
                        <a @click="() => scroll('showreel')" class="nav-link">HOME</a>
                        <a @click="() => scroll('editing')" class="nav-link">EDITING WORK</a>
                        <a @click="() => scroll('professional-information')" class="nav-link">PROFESSIONAL INFORMATION</a>
                        <a @click="() => scroll('about-me')" class="nav-link">ABOUT ME</a>
                        <a @click="() => scroll('contact-me')" class="nav-link">CONTACT ME</a>
                    </div>
                </Transition>
            </nav>
        </header>
    </Transition>
</template>