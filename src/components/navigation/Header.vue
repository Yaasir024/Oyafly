<script setup>
import { ref } from 'vue';
import MobileNav from '@/components/navigation/MobileNav.vue';

import { useClickOutside } from "@/composables/useClickOutside";


const mobileNav = ref(null)
const showMobileNav = ref(false)

useClickOutside(mobileNav, () => {
    showMobileNav.value = false;
});


const currencyNav = ref(null)
const showCurrencyNav = ref(false)

useClickOutside(currencyNav, () => {
    showCurrencyNav.value = false;
});

const currentCurrency = ref("NGN")

const currencies = ["NGN", "USD"]

const selectCurrency = (c) => {
    currentCurrency.value = c
    showCurrencyNav.value = false
}
</script>

<template>
    <header class="sticky top-0 bg-of-main pb-1 z-20">
        <section class="flex items-center justify-end py-[6px] pr-[24px]">
            <div class="text-[13px] hidden xs:block">Call support: +234-803-000-0031</div>
            <div class="text-[13px] font-semibold ml-4">Manage bookings</div>
            <div class="ml-4 relative" ref="currencyNav">
                <button class=" flex items-center" @click="showCurrencyNav = !showCurrencyNav">
                    <span class="text-[13px] font-semibold">
                        {{ currentCurrency }}
                    </span>
                    <svg class="ml-[4px]" width="10" height="7" viewBox="0 0 10 7" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M1.06798 0.333374C0.351977 0.333374 -0.0306894 1.17671 0.441311 1.71537L4.12198 5.92204C4.23148 6.04718 4.36647 6.14747 4.5179 6.21619C4.66932 6.2849 4.83369 6.32044 4.99998 6.32044C5.16626 6.32044 5.33063 6.2849 5.48206 6.21619C5.63349 6.14747 5.76848 6.04718 5.87798 5.92204L9.55931 1.71537C10.0306 1.17671 9.64798 0.333374 8.93264 0.333374H1.06731H1.06798Z"
                            fill="#10182C" />
                    </svg>
                </button>
                <transition name="menu">
                    <div class="absolute top-[20px] left-0 z-[5]" v-if="showCurrencyNav">
                        <ul class="bg-white border rounded-b-md">
                            <li class="px-2 py-2 cursor-pointer hover:bg-of-blue hover:text-white capitalize text-base font-medium"
                                v-for="currency in currencies" :key="currency" @click="selectCurrency(currency)">
                                {{ currency }}
                            </li>
                        </ul>
                    </div>
                </transition>
            </div>
        </section>
        <nav class="pl-[24px] pr-[12px] py-[12px]  flex items-center justify-between bg-white rounded-[20px]">
            <RouterLink to="/">
                <img src="/logo.svg" alt="" class="">
            </RouterLink>
            <div class="flex items-center border-l border-[#DCDADA] pl-[20px]">
                <ul class="hidden md:flex items-center mr-[20px]">
                    <li class="text-[16px] leading-[19px] mr-[20px]">
                        <RouterLink to="/about">About Us</RouterLink>
                    </li>
                    <li class="text-[16px] leading-[19px] mr-[20px]">
                        <RouterLink to="/contact-us">Contact Us</RouterLink>
                    </li>
                </ul>
                <div class="text-[16px] leading-[19px] font-semibold mr-[20px] hidden md:block">
                    <RouterLink to="/" class="font-semibold">Sign in</RouterLink>
                </div>
                <div class="hidden md:block">
                    <RouterLink to="/">
                        <button
                            class="px-[20px] py-[10px] rounded-[40px] text-white text-[16px] leading-[19px] font-bold bg-of-blue">Create
                            an account</button>
                    </RouterLink>
                </div>
                <div class="block md:hidden" ref="mobileNav">
                    <svg @click="showMobileNav = !showMobileNav" class="cursor-pointer" height="24" width="24"
                        clip-rule="evenodd" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2"
                        viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="m22 16.75c0-.414-.336-.75-.75-.75h-18.5c-.414 0-.75.336-.75.75s.336.75.75.75h18.5c.414 0 .75-.336.75-.75zm0-5c0-.414-.336-.75-.75-.75h-18.5c-.414 0-.75.336-.75.75s.336.75.75.75h18.5c.414 0 .75-.336.75-.75zm0-5c0-.414-.336-.75-.75-.75h-18.5c-.414 0-.75.336-.75.75s.336.75.75.75h18.5c.414 0 .75-.336.75-.75z"
                            fill-rule="nonzero" />
                    </svg>
                    <transition name="nav">
                        <MobileNav v-if="showMobileNav" @close="showMobileNav = false" />
                    </transition>
                </div>
            </div>
        </nav>
        <div class="overlay h-screen fixed top-0 left-0 bottom-0 right-0 bg-black/40 z-30" v-if="showMobileNav">
        </div>
    </header>
</template>

<style scoped>
/* Nav Animation */
.nav-enter-active,
.nav-leave-active {
    transition: all 0.4s ease;
}

.nav-enter-from,
.nav-leave-to {
    opacity: 0;
    transform: translateX(100%);
}
/* Menu Animation */
.menu-enter-active,
.menu-leave-active {
  transition: transform 0.3s ease;
  transform-origin: top left;
}

.menu-enter-from,
.menu-leave-to {
  transform: scale(0);
}
</style>