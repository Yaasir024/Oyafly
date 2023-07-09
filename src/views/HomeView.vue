<script setup>
import Header from '@/components/navigation/Header.vue';
import Hero from '@/components/home/Hero.vue';
import TopDeals from '@/components/home/TopDeals.vue';
import Explore from '@/components/home/Explore.vue';
import Perks from '@/components/home/Perks.vue';
import Footer from '@/components/navigation/Footer.vue';
</script>

<template>
  <main class="bg-of-main  min-h-screen">
    <div class="px-4 sm:px-6">
      <Header />
      <Hero />
      <TopDeals />
      <Explore />
      <Perks />
      <section class="mt-2 bg-white rounded-[20px] py-[30px] flex items-center justify-center">
        <div class="flex items-center">
          <h3 class="text-[18px] sm:text-[20px] leading-[21px] font-semibold font-pp">
            Manage your booking
          </h3>
          <svg class="ml-[16px]" width="52" height="38" viewBox="0 0 52 38" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M7.91 14.91C7.91 14.91 7.92 14.97 7.93 15L13.96 37.5H52L45.97 15C43.75 6.72 35.23 0 26.95 0H18.91C10.66 0 5.75 6.67 7.91 14.91Z"
              fill="#00EA8A" />
            <path
              d="M13.267 11.209C13.122 11.0778 12.9314 11.0084 12.7359 11.0157C12.5404 11.0229 12.3555 11.1063 12.2206 11.248C12.0857 11.3896 12.0115 11.5784 12.0138 11.774C12.0161 11.9696 12.0948 12.1566 12.233 12.295L18.484 18.25H3.75C3.55109 18.25 3.36032 18.329 3.21967 18.4697C3.07902 18.6103 3 18.8011 3 19C3 19.1989 3.07902 19.3897 3.21967 19.5303C3.36032 19.671 3.55109 19.75 3.75 19.75H18.484L12.233 25.704C12.0889 25.8411 12.0051 26.0299 12.0001 26.2288C11.9951 26.4277 12.0694 26.6204 12.2065 26.7645C12.3436 26.9087 12.5324 26.9924 12.7313 26.9974C12.9301 27.0024 13.1229 26.9281 13.267 26.791L20.687 19.724C20.8493 19.5699 20.955 19.3656 20.987 19.144C21.0053 19.0482 21.005 18.9497 20.986 18.854C20.9537 18.6332 20.848 18.4296 20.686 18.276L13.267 11.209Z"
              fill="#10182C" />
          </svg>
        </div>
      </section>

    </div>
    <Footer />
  </main>
</template>
