<script setup>
import { ref, computed } from 'vue'
// Import Swiper Vue.js components
import { Autoplay, Pagination, Navigation } from 'swiper/modules';
import { Swiper, SwiperSlide, useSwiper } from 'swiper/vue'

// Import Swiper styles
import 'swiper/css'
// import 'swiper/css/autoplay'


let swipfunc = null
const onSwiper = (swiper) => {
    swipfunc = swiper
}
const onSlideChange = () => { }

const modules = [Autoplay, Pagination, Navigation]
</script>

<template>
    <section class="mt-2 bg-white rounded-[20px] pt-[40px]">
        <div class="px-[24px]">
            <h1 class="text-[36px] sm:text-[48px] leading-[32px] sm:leading-[46px] font-pp font-semibold">
                Explore Nigeria
            </h1>
            <p class="text-[18px] sm:text-[24px] leading-[24px] sm:leading-[36px] max-w-[530px] mt-[12px]">
                Whether it’s your first flight or simply your latest, we work to anticipate your every need
            </p>
        </div>
        <div class="mt-[70px] px-[24px]">
            <swiper :space-between="16" :autoplay="{
                delay: 2500,
                disableOnInteraction: true,
            }" :breakpoints="{
    200: {
        slidesPerView: 1.4,
    },
    480: {
        slidesPerView: 2,
    },
    580: {
        slidesPerView: 2.8,
    },
    650: {
        slidesPerView: 3,
    },
    800: {
        slidesPerView: 4,
    },
    // when window width is >= 640px
    1000: {
        slidesPerView: 5,
    },
    1240: {
        slidesPerView: 5.6,
    }
}" :modules="modules" class="mySwiper">
                <swiper-slide>
                    <img src="@/assets/images/home/locations/lagos.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/abuja.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/asaba.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/akure.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/kano.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/lagos.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/abuja.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/asaba.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/akure.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/kano.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/lagos.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/abuja.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/asaba.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/akure.png" alt="" class="w-full">
                </swiper-slide>
                <swiper-slide>
                    <img src="@/assets/images/home/locations/kano.png" alt="" class="w-full">
                </swiper-slide>
            </swiper>
        </div>
        <div class="mt-[24px] px-[24px] pb-[24px] ">
            <div class="border-t border-[#D7E6FE] pt-[30px] flex items-center justify-end">
                <div class="flex items-center">
                    <h4 class="text-[18px] sm:text-[20px] leading-[21px] font-semibold font-pp mr-2">more trending
                        destinations</h4>
                    <svg width="47" height="38" viewBox="0 0 47 38" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M45.9909 14.91C45.9909 14.91 45.9809 14.97 45.9709 15L39.9409 37.5H1.90088L7.93088 15C10.1509 6.72 18.6709 0 26.9509 0H34.9909C43.2409 0 48.1509 6.67 45.9909 14.91Z"
                            fill="#00EA8A" />
                        <path
                            d="M13.767 11.209C13.622 11.0778 13.4314 11.0084 13.2359 11.0157C13.0404 11.0229 12.8555 11.1063 12.7206 11.248C12.5857 11.3896 12.5115 11.5784 12.5138 11.774C12.5161 11.9696 12.5948 12.1566 12.733 12.295L18.984 18.25H4.25C4.05109 18.25 3.86032 18.329 3.71967 18.4697C3.57902 18.6103 3.5 18.8011 3.5 19C3.5 19.1989 3.57902 19.3897 3.71967 19.5303C3.86032 19.671 4.05109 19.75 4.25 19.75H18.984L12.733 25.704C12.5889 25.8411 12.5051 26.0299 12.5001 26.2288C12.4951 26.4277 12.5694 26.6204 12.7065 26.7645C12.8436 26.9087 13.0324 26.9924 13.2313 26.9974C13.4301 27.0024 13.6229 26.9281 13.767 26.791L21.187 19.724C21.3493 19.5699 21.455 19.3656 21.487 19.144C21.5053 19.0482 21.505 18.9497 21.486 18.854C21.4537 18.6332 21.348 18.4296 21.186 18.276L13.767 11.209Z"
                            fill="#10182C" />
                    </svg>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.carousel::-webkit-scrollbar {
    display: none;
}

.carousel {
    box-shadow: -10px 0 10px -5px rgba(225, 225, 225, 0.5) inset;
}
</style>