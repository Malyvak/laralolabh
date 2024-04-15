<script lang="ts" setup>

import image1 from '@/assets/images/AboutMeLaraImage_1.jpg';
import image2 from '@/assets/images/AboutMeLaraImage_2.jpg';
import image3 from '@/assets/images/AboutMeLaraImage_3.jpg';

</script>

<template>
    <section id="about-me" class="about-me">
        <h1 class="title">ABOUT ME</h1>
        <div class="about-me-container">
            <div class="images-wrapper">
                <div class="image-container">
                    <img class="image-1" :src="image1"/>
                </div>
                <div class="image-container">
                    <img class="image-2" :src="image2"/>
                </div>
                <div class="image-container">
                    <img class="image-3" :src="image3"/>
                </div>
            </div>
            <div class="about-me-text">
                <p>
                    I have spent my life so far dedicated to chasing the arts, and can't wait to spend 
                    the rest uncovering more. My main passion for editing has led me to work with a 
                    vast range of creative individuals and projects with whom I have grown within the
                    Brisbane/Meanjin community and beyond.
                </p>
                <p>
                    When I'm not working with film, you might find me silversmithing, 
                    restoring gravestones, or painting and photographing for local bands. 
                    I'll never have a nice manicure, but I'll certainly never be bored!
                </p>
                <p>
                    Whether you're a fellow creator, or someone who needs one on
                    their team - I would love to work with you. Feel free to drop me a
                    line below and let's chat.
                </p>
            </div>
        </div>
    </section>
</template>