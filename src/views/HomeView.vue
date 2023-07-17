<script setup>
import Header from '@/components/navigation/Header.vue';
import Hero from '@/components/home/Hero.vue';
import AirlinesIcon from '@/components/global/AirlinesIcon.vue';
import TopDeals from '@/components/home/TopDeals.vue';
import Explore from '@/components/home/Explore.vue';
import Perks from '@/components/home/Perks.vue';
import ManageBooking from '@/components/global/ManageBooking.vue';
import Footer from '@/components/navigation/Footer.vue';
</script>

<template>
  <main class="bg-of-main  min-h-screen">
    <div class="px-4 sm:px-6">
      <Header />
      <Hero />
      <AirlinesIcon />
      <TopDeals />
      <Explore />
      <Perks />
      <ManageBooking />
    </div>
    <Footer />
  </main>
</template>
