<script setup>
import { ref, computed } from 'vue'

import { useClickOutside } from '@/composables/useClickOutside'

const emit = defineEmits(["close"]) 

const closeOnRoute = () => {
    emit('close')
}

const currentYear = computed(() => {
    const date = new Date();
    return date.getFullYear();
})

</script>

<!-- calc(100dvh-60px)
calc(100vh-100px) top-[60px]-->
<template>
    <div
        class="fixed h-[100dvh] sm:h-[100dvh] flex flex-col justify-between top-0 bottom-0 left-0 right-0 bg-white z-50 overflow-y-auto">
        <div class="">
            <div class="px-[20px] pt-4 pb-2 flex items-center justify-end">
                <button class="link" @click="closeOnRoute()">
                    <svg height="24" width="24" fill="currentColor" clip-rule="evenodd" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="m12 10.93 5.719-5.72c.146-.146.339-.219.531-.219.404 0 .75.324.75.749 0 .193-.073.385-.219.532l-5.72 5.719 5.719 5.719c.147.147.22.339.22.531 0 .427-.349.75-.75.75-.192 0-.385-.073-.531-.219l-5.719-5.719-5.719 5.719c-.146.146-.339.219-.531.219-.401 0-.75-.323-.75-.75 0-.192.073-.384.22-.531l5.719-5.719-5.72-5.719c-.146-.147-.219-.339-.219-.532 0-.425.346-.749.75-.749.192 0 .385.073.531.219z"/></svg>
                </button>
            </div>
            <ul class="px-[20px]">
                <li class="py-[25px] flex items-center justify-center px-2">
                    <RouterLink to="/about" class="link text-[24px] leading-[28px] tracking-[-0.24px] font-pp font-semibold" @click="closeOnRoute">About Us</RouterLink>
                </li>
                <li class="py-[25px] flex items-center justify-center px-2">
                    <RouterLink to="/contact-us" class="link text-[24px] leading-[28px] tracking-[-0.24px] font-pp font-semibold" @click="closeOnRoute">Contact Us</RouterLink>
                </li>
                <li class="py-[25px] flex items-center justify-center px-2">
                    <RouterLink to="/" class="link text-[24px] leading-[28px] tracking-[-0.24px] font-pp font-semibold" @click="closeOnRoute">Sign in</RouterLink>
                </li>
                <li class="mt-[12px]">
                    <RouterLink to="/" @click="closeOnRoute()">
                        <button class="py-[25px] px-2 w-full text-white text-[24px] leading-[28px] tracking-[-0.24px] bg-of-blue font-semibold font-pp rounded-[88px]">Create an account</button>
                    </RouterLink>
                </li>
            </ul>
        </div>
        <div class="">
            <div class="pt-[16px] px-[20px] pb-[24px] w-full bg-[#D7E6FE]">
                <h3 class="text-[16px] tracking-[0.18px] font-bold">
                    Subscribe for our special deals
                </h3>
                <h4 class="text-[18px] leading-[32px] tracking-[0.18px] mt-[4px]">
                    Save with our latest fares and offers.
                </h4>
                <div class="mt-[12px]">
                    <form @submit.prevent class="flex items-center sm:min-w-[400px] w-full bg-white rounded-xl p-[4px]">
                        <input type="text" placeholder="Your email address"
                            class="w-full text-[14px] leading-[25px] placeholder:text-of-dark placeholder:font-normal outline-none px-2 py-[5px]">
                        <button
                            class="ml-2 px-[8px] py-[5px] bg-of-dark rounded-lg text-[14px] text-white leading-[25px] font-semibold">Subscribe</button>
                    </form>
                </div>
                <p class="mt-[16px] text-base font-semibold font-inter text-[#FF3B4A]">
                    Please include an @ in
                    the email address</p>
            </div>
            <div class="bg-[#10182C]">
                <div class="px-[20px] py-[12px] flex items-center justify-between border-b border-white">
                    <a href="#" class="text-lg tracking-[0.18px] font-inter text-[#D7E6FE]">
                        Twitter
                    </a>
                    <a href="#" class="text-lg tracking-[0.18px] font-inter text-[#D7E6FE]">
                        LinkedIn
                    </a>
                    <a href="#" class="text-lg tracking-[0.18px] font-inter text-[#D7E6FE]">
                        Instagram
                    </a>
                </div>
                <div class="px-[20px] py-[10px] flex items-center justify-between">
                    <span class="text-[14px] leading-[17px] tracking-[0.28px] text-[#D7E6FE]">{{ currentYear }},
                        Resilience17</span>
                    <span class="text-[14px] leading-[17px] tracking-[0.28px] text-[#D7E6FE]">Design, <span
                            class="underline">Studio
                            Mbari</span></span>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.link {
    transition: all .3s ease;
}

.link:hover {
    color: #1549FF;
}
</style>