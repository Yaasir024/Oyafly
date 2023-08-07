<script setup>
import Header from '@/components/navigation/Header.vue';
import Hero from '@/components/contact/Hero.vue';
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
      <Feedback />
      <Perks />
      <ManageBooking />
    </div>
    <Footer />
  </main>
</template>
