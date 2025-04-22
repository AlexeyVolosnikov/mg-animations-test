<template>
    <div
      class="logo-wrapper pointerable pointerable-darker"
      :class="{ 'squares-only': isAnimateViaScroll && scrolledDown }"
    >
      <img class="text" src="@/assets/header/logo/mosgraf-text.svg" />
      <img class="squares" src="@/assets/header/logo/mosgraf-squares.svg" />
    </div>
</template>
  
<script>
  export default {
    name: 'Logo',
    props: {
      isAnimateViaScroll: {
        type: Boolean,
        default: false,
      },
    },
    data() {
      return {
        scrolledDown: false,
      };
    },
    mounted() {
      if (this.isAnimateViaScroll) {
        window.addEventListener('scroll', this.checkScroll);
        this.checkScroll(); // чтобы сработало при загрузке
      }
    },
    beforeUnmount() {
      if (this.isAnimateViaScroll) {
        window.removeEventListener('scroll', this.checkScroll);
      }
    },
    methods: {
      checkScroll() {
        this.scrolledDown = window.scrollY > 0;
      },
    },
  };
</script>

<style scoped lang="scss">
$transition: 0.4s;

.logo-wrapper {
    position: relative;
    max-width: 118px;
    height: 27px;
    display: flex;
    align-items: flex-end;
  
    &.squares-only {
      .text {
        transform: translateX(-120%);
        opacity: 0;
        transition: $transition;
      }
  
      .squares {
        transform: translateX(-92px);
        height: 27px;
        max-width: 27px;
        right: 0;
        top: 0;
        transition: $transition;
      }
    }
  }
  
  .text {
    max-width: 106.81px;
    width: 100%;
  }
  .squares {
    max-width: 11.87px;
    width: 100%;
    position: absolute;
    right: -13px;
    top: 0;
    transition: 0.25s;
  }
</style>
  