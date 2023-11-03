<script lang="ts" setup>
import VideoComponent from '@/components/VideoComponent.vue';

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

</script>

<template>
    <section class="editing">

        <h1 class="title">EDITING WORK</h1>

        <div class="projects">
            <VideoComponent
                :image="image1"
                title="'Girls on Fire' webseries"
                description="Webseries teaser trailer"
            />
            <VideoComponent
                :image="image2"
                title="Blonded 'Love is a Gun' single launch"
                description="Promotional marketing piece"
            />
            <VideoComponent
                :image="image3"
                title="Girl Shaped Flames 'Camp Courage'"
                description="Event promo"
            />
            <VideoComponent
                :image="image4"
                title="'Village of Light'"
                description="Event advertisement"
            />
            <VideoComponent
                :image="image5"
                title="The World's Biggest Garage Sale 'Responsible Re-Fit'"
                description="Marketing campaign (made in association with Connect Creative)"
            />

            <VideoComponent
                :image="image6"
                title="SixPivot 'Passion'"
                description="Brand marketing piece"
            />
            <VideoComponent
                :image="image7"
                title="Ky Furneaux 'Aussie in Action'"
                description="Personal brand showreel"
            />
            <VideoComponent
                :image="image8"
                title="The World's Biggest Garage Sale 'Mickey Box'"
                description="Product launch advertisement (made in association with Connect Creative)"
            />
            <VideoComponent
                :image="image9"
                title="Blonded 'Out Cold'"
                description="Brand marketing piece"
            />
            <VideoComponent
                :image="image10"
                title="'A Frog's Short Day Out"
                description="PoC short animation"
            />
        </div>
    </section>
</template>