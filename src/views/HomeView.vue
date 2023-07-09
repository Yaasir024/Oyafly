<script setup>
import Header from '@/components/navigation/Header.vue';
import Hero from '@/components/home/Hero.vue';
import TopDeals from '@/components/home/TopDeals.vue';
import Explore from '@/components/home/Explore.vue';
</script>

<template>
  <main class="bg-of-main px-6 min-h-screen pb-[200px]">
    <Header />
    <Hero />
    <TopDeals />
    <Explore />
  </main>
</template>
