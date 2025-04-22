<template>
    <div>
        <MHeader
            :is-animate-via-scroll="true"
        />
        <BigMainBlock />
        <ParallaxSection
            :bg-image="ParallaxBgImage"
            title="Lorem Ipsum is simply dummy"
            subtitle="Lorem Ipsum is simply dummy text of the printing "
            :bg-speed="0.5"
            :content-speed="0.2"
        />
        <ListDirecitons
            title="How we can help"
            :items="[
                {
                    title: '3D Visualization',
                    text: `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s`
                },
                {
                    title: 'Animation + Video',
                    text: `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s`
                },
                {
                    title: 'VR/AR',
                    text: `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s`
                },
                {
                    title: 'Tour 360',
                    text: `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s`
                },
                {
                    title: 'Digital',
                    text: `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s`
                }
            ]"
        />
    </div>
</template>

<script>
import MHeader from '@/components/MHeader.vue';
import BigMainBlock from '@/components/BigMainBlock.vue';
import ListDirecitons from '@/components/List/Directions.vue';
import ParallaxSection from '@/components/helpers/ParallaxSection.vue';
import ParallaxBgImage from '@/assets/index/parallax-block-bg.jpg'

export default {
    components: {
        BigMainBlock,
        MHeader,
        ParallaxSection,
        ListDirecitons
    },
    data () {
        return {
            ParallaxBgImage
        }
    }
}
</script>

<style scoped lang="scss"></style>