<script setup>
import 'vue3-carousel/dist/carousel.css';
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel';
import WhatsappIcon from '~/assets/icons/WhatsappIcon.vue';
import InstagramIcon from '~/assets/icons/InstagramIcon.vue';
import FacebookIcon from '~/assets/icons/FacebookIcon.vue';
import TelephoneIcon from '~/assets/icons/TelephoneIcon.vue';

const config = {
  autoplay: 3000,
  wrapAround: true,
  pauseAutoplayOnHover: true,
};
</script>

<template>
  <Carousel v-bind="config">
    <Slide v-for="slide in 2" :key="slide">
      <div class="carousel__item w-full">

        <div v-if="slide == 1" class="min-h-screen bg-home-first bg-cover bg-center">
          <div
            class="bg-gradient-to-b from-[#00000081] to-[#00000081] h-screen flex flex-col gap-5 lg:gap-3 justify-center items-center px-8 lg:px-36">

            <div class="px-2 py-2 backdrop-blur-md bg-white/30 rounded-lg">
              <img src="../assets/images/JM-logo.png" class="w-80" alt="">
            </div>

            <p class="text-white font-light text-xl underline decoration-[#FAF900] underline-offset-4">
              Desde 1999 levando o melhor para o seu negócio
            </p>

            <div class="flex text-white items-end gap-1 px-4">
              <NuxtLink to="/">
                <WhatsappIcon class="w-10 fill-white transition duration-300 ease-in-out hover:scale-125" />
              </NuxtLink>

              <NuxtLink to="/">
                <InstagramIcon class="w-10 fill-white transition duration-300 ease-in-out hover:scale-125" />
              </NuxtLink>

              <NuxtLink to="/">
                <FacebookIcon class="w-10 fill-white transition duration-300 ease-in-out hover:scale-125" />
              </NuxtLink>

              <NuxtLink to="/">
                <TelephoneIcon class="w-10 transition duration-300 ease-in-out hover:scale-125" />
              </NuxtLink>
            </div>

          </div>
        </div>

        <div v-else class="min-h-screen bg-home-second bg-cover bg-center">
          <div
            class="bg-gradient-to-b from-[#00000081] to-[#00000081] h-screen flex flex-col lg:flex-row gap-10 justify-center lg:justify-between items-center px-8 lg:px-36">

            <div class="space-y-5 lg:w-96 text-start order-2 lg:order-1">
              <p class="text-white font-bold text-3xl">Distribuidora PepsiCo</p>

              <p class="text-white font-light">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et
                dolore magna aliqua.
              </p>
            </div>

            <div class="order-1 lg:order-2">
              <img
                src="https://th.bing.com/th/id/R.ddee3fbffe75debdd5c40a664fa81841?rik=lMsZuzs%2btsCvjg&pid=ImgRaw&r=0"
                class="w-60 bg-white rounded-md p-8" alt="">
            </div>

          </div>
        </div>

      </div>
    </Slide>

    <template #addons>
      <Navigation />
      <Pagination />
    </template>
  </Carousel>
</template>

<style>
.bg-home-first {
  background-image: url('../assets/images/home-armazem.jpg');
}

.bg-home-second {
  background-image: url('https://www.arabianbusiness.com/cloud/2021/09/15/np5yYxq7-PepsiCo-food-and-beverage-768x335.jpg');
}
</style>
