<template>
    <section class="parallax-section" ref="parallaxRef">
        <div class="container">
            <div class="parallax-bg" :style="bgStyle"></div>
            <div class="parallax-content" :style="contentStyle">
                <h1 class="parallax-title">{{ title }}</h1>
                <p class="parallax-subtitle">{{ subtitle }}</p>
            </div>
        </div>
    </section>
</template>
  
<script>
  export default {
    props: {
      bgImage: {
        type: String,
        required: true
      },
      title: {
        type: String,
        required: true
      },
      subtitle: {
        type: String,
        required: true
      },
      bgSpeed: {
        type: Number,
        default: 0.5
      },
      contentSpeed: {
        type: Number,
        default: 0.2
      }
    },
    data() {
      return {
        scrollY: 0,
        bgStyle: {},
        contentStyle: {}
      }
    },
    mounted() {
      window.addEventListener('scroll', this.handleScroll)
      this.handleScroll() // Инициализация при загрузке
    },
    beforeUnmount() {
      window.removeEventListener('scroll', this.handleScroll)
    },
    methods: {
      handleScroll() {
        if (this.$refs.parallaxRef) {
          const rect = this.$refs.parallaxRef.getBoundingClientRect()
          const offset = window.pageYOffset - rect.top
          this.scrollY = offset
  
          // Параллакс эффект для фона
          this.bgStyle = {
            transform: `translateY(${this.scrollY * this.bgSpeed}px)`,
            backgroundImage: `url(${this.bgImage})`
          }
  
          // Параллакс эффект для контента
          this.contentStyle = {
            transform: `translateY(${this.scrollY * this.contentSpeed}px)`
          }
        }
      }
    }
  }
</script>

<style scoped lang="scss">
  .parallax-section {
    position: relative;
    height: 100vh;
    width: 100%;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: left;
  }
  
  .parallax-bg {
    position: absolute;
    top: -50vh; // смещаем вверх на половину увеличенной высоты
    left: 0;
    width: 100%;
    height: 200vh;
    background-size: cover;
    background-position: center;
    will-change: transform;
    z-index: 1;
  }
  
  .parallax-content {
    position: relative;
    z-index: 2;
    color: white;
    text-align: left;
    max-width: 800px;
    will-change: transform;
  }
  
  .parallax-title {
    font-size: 3rem;
    font-weight: 700;
    margin-bottom: 1rem;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
  }
  
  .parallax-subtitle {
    font-size: 1.5rem;
    text-shadow: 0 2px 5px rgba(0, 0, 0, 0.5);
  }
  
  @media (max-width: 768px) {
    .parallax-title {
      font-size: 2rem;
    }
    
    .parallax-subtitle {
      font-size: 1.2rem;
    }
  }
</style>