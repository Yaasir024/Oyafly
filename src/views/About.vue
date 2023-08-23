<script setup>
import Header from '@/components/navigation/Header.vue';
import Hero from '@/components/about/Hero.vue';
import AirlinesIcon from '@/components/global/AirlinesIcon.vue';
import AboutUs from '@/components/about/Us.vue';
import Values from '@/components/about/Values.vue';
import TopDeals from '@/components/home/TopDeals.vue';
import Feedback from '@/components/about/Feedback.vue';
import Perks from '@/components/home/Perks.vue';
import ManageBooking from '@/components/global/ManageBooking.vue';
import Footer from '@/components/navigation/Footer.vue';
</script>

<template>
  <main class="bg-of-main  min-h-screen">
    <div class="px-4 sm:px-6">
      <Header />
      <Hero />
      <AboutUs />
      <AirlinesIcon />
      <Values />
      <TopDeals />
      <Feedback />
      <Perks />
      <ManageBooking />
    </div>
    <Footer />
  </main>
</template>
