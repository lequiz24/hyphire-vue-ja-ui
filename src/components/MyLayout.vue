<!-- MyLayout.vue -->
<template>
  <q-layout>
    <!-- Header -->
    <q-header>
      <q-toolbar>
        <q-btn flat round dense icon="menu" @click="toggleMenu" />
        <q-toolbar-title> Robin Website </q-toolbar-title>
        <q-btn flat dense label="Profile" />
        <q-btn flat dense label="Settings" />
        <q-btn flat dense label="Logout" />
      </q-toolbar>
      <!-- <q-menu ref="menu" anchor="top right">
        <q-list>
          <q-item clickable @click="goToPage('/home')">Home</q-item>
          <q-item clickable @click="goToPage('/about')">About</q-item>
          <q-item clickable @click="goToPage('/contact')">Contact</q-item>
        </q-list>
      </q-menu> -->
    </q-header>

    <!-- Body -->
    <q-page-container>
      <!-- Animation -->
      <q-page-sticky>
        <q-page-sticky-content>
          <q-fade-transition appear>
            <div class="animated-item">
              <h2>Welcome to Our Website!</h2>
              <p>Explore our amazing features and services.</p>
            </div>
          </q-fade-transition>
        </q-page-sticky-content>
      </q-page-sticky>

      <!-- Carousel -->
      <q-carousel arrows control navigation autoplay infinite :height="200">
        <q-carousel-slide
          v-for="(slide, index) in slides"
          :key="index"
          :img-src="slide.imgSrc"
          :img-alt="slide.imgAlt"
          :caption="slide.caption"
        />
      </q-carousel>

      <!-- Slider -->
      <q-slider v-model="sliderValue" />
    </q-page-container>

    <!-- Bottom -->
    <q-footer> Footer Content </q-footer>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      sliderValue: 50,
      slides: [
        {
          imgSrc: "/assets/slide1.jpg",
          imgAlt: "Slide 1",
          caption: "First slide",
        },
        {
          imgSrc: "/assets/slide2.jpg",
          imgAlt: "Slide 2",
          caption: "Second slide",
        },
        {
          imgSrc: "/assets/slide3.jpg",
          imgAlt: "Slide 3",
          caption: "Third slide",
        },
      ],
    };
  },
  methods: {
    toggleMenu() {
      this.$refs.menu.toggle();
    },
    goToPage(route) {
      this.$router.push(route);
    },
  },
};
</script>

<style scoped>
.animated-item {
  animation: fadeInUp 1s;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
