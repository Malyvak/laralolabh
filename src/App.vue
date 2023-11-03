<script lang="ts" setup>
import ShowReel from '@/views/ShowReel.vue';
import Editing from '@/views/Editing.vue';
import ProfessionalInformation from './views/ProfessionalInformation.vue';
import AboutMe from './views/AboutMe.vue';
import ContactMe from './views/ContactMe.vue';

import logo from '@/assets/images/header-logo.png'

</script>

<template>
    <header class="header">
        <nav class="navbar">
            <img class="brand" :src="logo"/>
            <div class="nav-links">
                <a href="#" class="nav-link">HOME</a>
                <a href="#" class="nav-link">EDITING WORK</a>
                <a href="#" class="nav-link">PROFESSIONAL INFORMATION</a>
                <a href="#" class="nav-link">ABOUT ME</a>
                <a href="#" class="nav-link">CONTACT ME</a>
            </div>
        </nav>
    </header>
    <ShowReel/>
    <Editing/>
    <ProfessionalInformation/>
    <AboutMe/>
    <ContactMe/>

</template>