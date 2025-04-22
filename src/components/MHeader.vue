<template>
    <div class="header-sticky">
        <div class="container">
            <div class="header-wrapper">
                <Logo
                    :is-animate-via-scroll="true"
                />
                <Hamburger />
            </div>
        </div>
    </div>
</template>

<script>
import Logo from '@/components/Logo.vue'
import Hamburger from '@/components/Hamburger.vue'

export default {
    components: {
        Logo,
        Hamburger
    },
    props: {
      isAnimateViaScroll: {
        type: Boolean,
        default: false,
      },
    }
}
</script>

<style scoped lang="scss">
.header-sticky {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    overflow: hidden;
    z-index: 10;
}
.header-wrapper {
    display: flex;
    justify-content: space-between;
    padding-top: 20px;
    padding-bottom: 20px;
}
</style>