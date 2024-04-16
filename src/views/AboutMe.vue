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
                    So far I've spent all my work time, downtime, and everything in between chasing the arts, 
                    and I look forward to continuing to do so in new and different ways every day.
                </p>
                <p>
                    On the weekend you might find me photographing for local gigs, hosting painting classes, 
                    restoring headstones, holding local art exhibitions, or dodgily silversmithing. 
                    I'll never have a nice manicure but I doubt I'll ever be bored…
                </p>
                <p>
                    Whether you're a fellow creator, or someone who needs one on their team - 
                    I would love to work with you. Feel free to drop me a line below and let's chat.
                </p>
            </div>
        </div>
    </section>
</template>