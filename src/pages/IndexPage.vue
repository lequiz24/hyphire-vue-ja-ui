<template>
  <q-page class="flex flex-center">
    <!-- let put carousel here  -->
    <div id="q-app" style="min-height: 30vh">
      <div class="q-pa-md">
        <q-carousel
          v-model="slide"
          vertical
          transition-prev="slide-down"
          transition-next="slide-up"
          swipeable
          animated
          control-color="white"
          navigation-icon="radio_button_unchecked"
          navigation
          padding
          arrows
          height="300px"
          class="bg-black text-white shadow-1 rounded-borders"
        >
          <q-carousel-slide name="style" class="column no-wrap flex-center">
            <q-icon name="style" size="56px"></q-icon>
            <div class="q-mt-md text-center">
              {{ details }}
            </div>
          </q-carousel-slide>
          <q-carousel-slide name="tv" class="column no-wrap flex-center">
            <q-icon name="live_tv" size="56px"></q-icon>
            <div class="q-mt-md text-center">
              {{ details }}
            </div>
          </q-carousel-slide>
          <q-carousel-slide name="layers" class="column no-wrap flex-center">
            <q-icon name="layers" size="56px"></q-icon>
            <div class="q-mt-md text-center">
              {{ details }}
            </div>
          </q-carousel-slide>
          <q-carousel-slide name="map" class="column no-wrap flex-center">
            <q-icon name="terrain" size="56px"></q-icon>
            <div class="q-mt-md text-center">
              {{ details }}
            </div>
          </q-carousel-slide>
        </q-carousel>
      </div>
    </div>

    <!-- slider -->

    <div id="q-app" style="min-height: 20vh">
      <div class="q-pa-md">
        <q-badge color="black"> SLIDER: {{ lazy }} </q-badge>

        <q-slider
          :model-value="lazy"
          @change="
            (val) => {
              lazy = val;
            }
          "
          :min="0"
          :max="45"
          :step="5"
          color="black"
          label
        ></q-slider>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref, createApp } from "vue";
import { Quasar } from "quasar";

const slide = ref("style");
const details = "This is a couresel functonality I am testing  ";

const app = createApp({
  setup() {
    return {
      slide,

      details,
      lazy: ref(6),
    };
  },
});

app.use(Quasar, { config: {} });

defineOptions({
  name: "IndexPage",
});
</script>
