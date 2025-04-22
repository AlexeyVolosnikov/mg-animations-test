<template>
    <div class="big-main-block big-main-block-bg" ref="mainBlock">
      <div class="big-main-block">
        <div class="titles container">
          <transition-group name="fade" tag="div">
            <h1
              v-for="(item, index) in titles"
              :key="`title-${index}`"
              :class="[
                'fade-item',
                { 'visible': isVisible, 'fade-out': isHalfHidden }
              ]"
              :style="{ transitionDelay: `${index * 100}ms` }"
            >
              {{ item }}
            </h1>
          </transition-group>
        </div>
      </div>
    </div>
</template>
  
<script>
  export default {
    data() {
      return {
        titles: ['3D visualization', 'Animation', 'VR/AR', 'Tour 360', 'Digital', 'Video'],
        isVisible: false,
        isHalfHidden: false,
        observer: null,
      };
    },
    mounted() {
      // Появление при загрузке
      setTimeout(() => {
        requestAnimationFrame(() => {
            this.isVisible = true;
        });
    
        // IntersectionObserver с порогом 50%
        this.observer = new IntersectionObserver(
            ([entry]) => {
            this.isHalfHidden = !entry.isIntersecting;
            },
            {
            root: null,
            threshold: 0.66, // 1\3 экрана
            }
        );
    
        if (this.$refs.mainBlock) {
            this.observer.observe(this.$refs.mainBlock);
        }
      }, 250)
    },
    beforeUnmount() {
      if (this.observer && this.$refs.mainBlock) {
        this.observer.unobserve(this.$refs.mainBlock);
      }
    },
  };
  </script>
  
  <style scoped lang="scss">
  .big-main-block-bg {
    width: 100%;
    background: url('@/assets/index/first-block-bg.jpg') no-repeat center center;
    background-size: cover;
  }
  .big-main-block {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100vh;
    padding-bottom: 60px;
  
    .titles {
      margin-top: auto;
  
      h1.fade-item {
        opacity: 0;
        transform: translateY(30px);
        transition: opacity 0.6s ease, transform 0.6s ease;
  
        &.visible {
          opacity: 1;
          transform: translateY(0);
        }
  
        &.fade-out {
          opacity: 0;
          transform: translateY(-20px);
          transition: opacity 0.4s ease, transform 0.4s ease;
        }
  
        color: #fff;
        font-size: 70px;
        font-style: normal;
        font-weight: 700;
        line-height: normal;
        text-transform: uppercase;
  
        &:not(:last-child) {
          margin-bottom: 4px;
        }
      }
    }
  }
  </style>
  