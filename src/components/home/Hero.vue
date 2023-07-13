<script setup>
import { ref, onMounted, computed, shallowRef, h } from 'vue';
import { useRouter } from 'vue-router';

import HeroFilter from '@/components/home/HeroFilter.vue'
import { useClickOutside } from "@/composables/useClickOutside";

let flightClasses = ["first class", "business", "economy"]

const flightData = ref({
    type: "round",
    class: "economy",
    adult: 1,
    infants: 0
})
const flightClassMenu = ref(null)
const showFlightClassMenu = ref(false)

useClickOutside(flightClassMenu, () => {
    showFlightClassMenu.value = false;
});

const selectClass = (c) => {
    flightData.value.class = c
    showFlightClassMenu.value = false
}
const reduceAdult = () => {
    if (flightData.value.adult != 0) {
        flightData.value.adult -= 1
    }
}
const reduceInfant = () => {
    if (flightData.value.infants != 0) {
        flightData.value.infants -= 1
    }
}
</script>

<template>
    <section class="mt-[10px] ">
        <section class="relative pl-[24px] pt-[40px] pb-[28px] bg-white rounded-[20px] overflow-x-hidden">
            <div class="flex justify-between lg:overflow-x-hidden">
                <div class="">
                    <h1
                        class="text-[52px] sm:text-[68px] md:text-[96px] leading-[48px] sm:leading-[62px] md:leading-[92px] font-semibold font-pp max-w-[540px]">
                        Going
                        somewhere?
                    </h1>
                    <p class="mt-[12px] text-[18px] sm:text-[24px] leading-[22px] sm:leading-[36px] max-w-[490px]">
                        Create unforgettable travel experiences all the way there and back, with ease.
                    </p>

                </div>
                <img src="@/assets/images/home/hero-cloud.svg" alt="" class="mt-[45px] hidden">
            </div>
            <div class="mt-[60px]">
                <div class="flex sm:items-center flex-col sm:flex-row">
                    <div class="flex items-center mb-4 sm:mb-0  flex-wrap gap-y-1">
                        <button
                            class="px-[12px] py-[10px] border border-of-dark rounded-[40px] text-[16px] leading-[19px] font-semibold mr-[16px] transition-all duration-200 ease-in-out"
                            :class="flightData.type == 'one-way' ? 'bg-of-dark text-[#D7E6FE]' : ''"
                            @click="flightData.type = 'one-way'">One-way</button>
                        <button
                            class="px-[12px] py-[10px] border border-of-dark rounded-[40px] text-[16px] leading-[19px] font-semibold mr-[16px] transition-all duration-200 ease-in-out"
                            :class="flightData.type == 'round' ? 'bg-of-dark text-[#D7E6FE]' : ''"
                            @click="flightData.type = 'round'">Return
                            trip</button>
                        <div class="mr-[4px] relative" ref="flightClassMenu">
                            <button @click="showFlightClassMenu = !showFlightClassMenu"
                                class="px-[12px] py-[10px] border border-of-dark rounded-[40px] mr-[16px] flex items-center">
                                <span class="text-[16px] leading-[19px] font-semibold capitalize mr-[4px]">{{
                                    flightData.class }}</span>
                                <svg width="10" height="7" viewBox="0 0 10 7" fill="none"
                                    xmlns="http://www.w3.org/2000/svg">
                                    <path
                                        d="M1.06798 0.333374C0.351977 0.333374 -0.0306894 1.17671 0.441311 1.71537L4.12198 5.92204C4.23148 6.04718 4.36647 6.14747 4.5179 6.21619C4.66932 6.2849 4.83369 6.32044 4.99998 6.32044C5.16626 6.32044 5.33063 6.2849 5.48206 6.21619C5.63349 6.14747 5.76848 6.04718 5.87798 5.92204L9.55931 1.71537C10.0306 1.17671 9.64798 0.333374 8.93264 0.333374H1.06731H1.06798Z"
                                        fill="#10182C" />
                                </svg>

                            </button>
                            <transition name="menu">
                                <div class="absolute top-[50px] left-0 w-full z-[5]" v-if="showFlightClassMenu">
                                    <ul class="bg-white border rounded-b-md">
                                        <li class="px-2 py-2 cursor-pointer hover:bg-of-blue hover:text-white capitalize text-base font-medium"
                                            v-for="fclass in flightClasses" :key="fclass" @click="selectClass(fclass)">
                                            {{ fclass }}
                                        </li>
                                    </ul>
                                </div>
                            </transition>
                        </div>
                    </div>
                    <div class="flex items-center">
                        <button class="subtract mr-2" @click="reduceAdult">
                            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M10 0C15.523 0 20 4.477 20 10C20 15.523 15.523 20 10 20C4.477 20 0 15.523 0 10C0 4.477 4.477 0 10 0ZM10 1.5C7.74566 1.5 5.58365 2.39553 3.98959 3.98959C2.39553 5.58365 1.5 7.74566 1.5 10C1.5 12.2543 2.39553 14.4163 3.98959 16.0104C5.58365 17.6045 7.74566 18.5 10 18.5C12.2543 18.5 14.4163 17.6045 16.0104 16.0104C17.6045 14.4163 18.5 12.2543 18.5 10C18.5 7.74566 17.6045 5.58365 16.0104 3.98959C14.4163 2.39553 12.2543 1.5 10 1.5ZM14.25 9.25C14.4489 9.25 14.6397 9.32902 14.7803 9.46967C14.921 9.61032 15 9.80109 15 10C15 10.1989 14.921 10.3897 14.7803 10.5303C14.6397 10.671 14.4489 10.75 14.25 10.75H5.75C5.55109 10.75 5.36032 10.671 5.21967 10.5303C5.07902 10.3897 5 10.1989 5 10C5 9.80109 5.07902 9.61032 5.21967 9.46967C5.36032 9.32902 5.55109 9.25 5.75 9.25H14.25Z"
                                    fill="#10182C" />
                            </svg>
                        </button>
                        <span class="leading-[19px] font-semibold">{{ flightData.adult }} adult</span>
                        <button class="add ml-2 mr-2" @click="flightData.adult++">
                            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M10 0C15.523 0 20 4.477 20 10C20 15.523 15.523 20 10 20C4.477 20 0 15.523 0 10C0 4.477 4.477 0 10 0ZM10 1.5C7.74566 1.5 5.58365 2.39553 3.98959 3.98959C2.39553 5.58365 1.5 7.74566 1.5 10C1.5 12.2543 2.39553 14.4163 3.98959 16.0104C5.58365 17.6045 7.74566 18.5 10 18.5C12.2543 18.5 14.4163 17.6045 16.0104 16.0104C17.6045 14.4163 18.5 12.2543 18.5 10C18.5 7.74566 17.6045 5.58365 16.0104 3.98959C14.4163 2.39553 12.2543 1.5 10 1.5ZM10 5C10.1989 5 10.3897 5.07902 10.5303 5.21967C10.671 5.36032 10.75 5.55109 10.75 5.75V9.25H14.25C14.4489 9.25 14.6397 9.32902 14.7803 9.46967C14.921 9.61032 15 9.80109 15 10C15 10.1989 14.921 10.3897 14.7803 10.5303C14.6397 10.671 14.4489 10.75 14.25 10.75H10.75V14.25C10.75 14.4489 10.671 14.6397 10.5303 14.7803C10.3897 14.921 10.1989 15 10 15C9.80109 15 9.61032 14.921 9.46967 14.7803C9.32902 14.6397 9.25 14.4489 9.25 14.25V10.75H5.75C5.55109 10.75 5.36032 10.671 5.21967 10.5303C5.07902 10.3897 5 10.1989 5 10C5 9.80109 5.07902 9.61032 5.21967 9.46967C5.36032 9.32902 5.55109 9.25 5.75 9.25H9.25V5.75C9.25 5.55109 9.32902 5.36032 9.46967 5.21967C9.61032 5.07902 9.80109 5 10 5Z"
                                    fill="#10182C" />
                            </svg>
                        </button>
                        <button class="subtract mr-2" @click="reduceInfant">
                            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M10 0C15.523 0 20 4.477 20 10C20 15.523 15.523 20 10 20C4.477 20 0 15.523 0 10C0 4.477 4.477 0 10 0ZM10 1.5C7.74566 1.5 5.58365 2.39553 3.98959 3.98959C2.39553 5.58365 1.5 7.74566 1.5 10C1.5 12.2543 2.39553 14.4163 3.98959 16.0104C5.58365 17.6045 7.74566 18.5 10 18.5C12.2543 18.5 14.4163 17.6045 16.0104 16.0104C17.6045 14.4163 18.5 12.2543 18.5 10C18.5 7.74566 17.6045 5.58365 16.0104 3.98959C14.4163 2.39553 12.2543 1.5 10 1.5ZM14.25 9.25C14.4489 9.25 14.6397 9.32902 14.7803 9.46967C14.921 9.61032 15 9.80109 15 10C15 10.1989 14.921 10.3897 14.7803 10.5303C14.6397 10.671 14.4489 10.75 14.25 10.75H5.75C5.55109 10.75 5.36032 10.671 5.21967 10.5303C5.07902 10.3897 5 10.1989 5 10C5 9.80109 5.07902 9.61032 5.21967 9.46967C5.36032 9.32902 5.55109 9.25 5.75 9.25H14.25Z"
                                    fill="#10182C" />
                            </svg>
                        </button>
                        <span class="leading-[19px] font-semibold">{{ flightData.infants }} infants</span>
                        <button class="add ml-2" @click="flightData.infants++">
                            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M10 0C15.523 0 20 4.477 20 10C20 15.523 15.523 20 10 20C4.477 20 0 15.523 0 10C0 4.477 4.477 0 10 0ZM10 1.5C7.74566 1.5 5.58365 2.39553 3.98959 3.98959C2.39553 5.58365 1.5 7.74566 1.5 10C1.5 12.2543 2.39553 14.4163 3.98959 16.0104C5.58365 17.6045 7.74566 18.5 10 18.5C12.2543 18.5 14.4163 17.6045 16.0104 16.0104C17.6045 14.4163 18.5 12.2543 18.5 10C18.5 7.74566 17.6045 5.58365 16.0104 3.98959C14.4163 2.39553 12.2543 1.5 10 1.5ZM10 5C10.1989 5 10.3897 5.07902 10.5303 5.21967C10.671 5.36032 10.75 5.55109 10.75 5.75V9.25H14.25C14.4489 9.25 14.6397 9.32902 14.7803 9.46967C14.921 9.61032 15 9.80109 15 10C15 10.1989 14.921 10.3897 14.7803 10.5303C14.6397 10.671 14.4489 10.75 14.25 10.75H10.75V14.25C10.75 14.4489 10.671 14.6397 10.5303 14.7803C10.3897 14.921 10.1989 15 10 15C9.80109 15 9.61032 14.921 9.46967 14.7803C9.32902 14.6397 9.25 14.4489 9.25 14.25V10.75H5.75C5.55109 10.75 5.36032 10.671 5.21967 10.5303C5.07902 10.3897 5 10.1989 5 10C5 9.80109 5.07902 9.61032 5.21967 9.46967C5.36032 9.32902 5.55109 9.25 5.75 9.25H9.25V5.75C9.25 5.55109 9.32902 5.36032 9.46967 5.21967C9.61032 5.07902 9.80109 5 10 5Z"
                                    fill="#10182C" />
                            </svg>
                        </button>
                    </div>
                </div>
            </div>
            <div class=" hidden xl:flex absolute right-[-100px] top-0 bottom-0">
                <div class="w-[300px] h-full bg-blue-500 clip-paralel mr-6">
                    <img src="@/assets/images/home/hero/cloud-1.png" alt="" class="h-full max-w-[700px] cloud-img ">

                </div>
                <div class="w-[300px] h-full bg-blue-500 clip-paralel">
                    <img src="@/assets/images/home/hero/cloud-2.png" alt="" class="h-full max-w-[700px] cloud-img ">
                </div>
            </div>
        </section>
        <HeroFilter />


    </section>
</template>

<style scoped>
.clip-paralel {
    clip-path: polygon(25% 0%, 100% 0%, 75% 100%, 0% 100%);
}

.cloud-img {
  animation: scrollAnimation 10s linear infinite;
}

@keyframes scrollAnimation {
    0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-150px);
  }
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

