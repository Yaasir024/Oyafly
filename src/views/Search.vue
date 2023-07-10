<script setup>
import { ref } from "vue"
import Header from '@/components/navigation/Header.vue';
import Hero from '@/components/home/Hero.vue';
import Footer from '@/components/navigation/Footer.vue';

import { useClickOutside } from "@/composables/useClickOutside";


const stops = ref(["any"])
const showStops = ref(true)
const airlines = ref(["any"])
const showAirlines = ref(true)
const cabin = ref(["any"])
const showCabin = ref(true)


let sortOptions = ["cheapest", "fastest", "reccomended"]

const sortMenu = ref(null)
const showSortMenu = ref(false)

const sortQuery = ref("cheapest")

useClickOutside(sortMenu, () => {
    showSortMenu.value = false;
});
const selectSortVal = (c) => {
    sortQuery.value = c
    showSortMenu.value = false
}
</script>

<template>
    <main class="bg-of-main  min-h-screen">
        <div class="px-4 sm:px-6">
            <Header />
            <Hero />
            <section class="flex mt-[44px]">
                <div class="w-full 2xl:w-[350px] pl-[24px] pr-[28px] 2xl:shrink-0">
                    <h3 class="text-[20px] leading-[19px] font-semibold font-pp">Filter your results</h3>
                    <div class="mt-[24px] max-w-[200px]">
                        <div class="flex items-center justify-between pb-2 border-b border-[#10182C33]"
                            @click="showStops = !showStops">
                            <span class="text-[16px] leading-[19px] font-medium">Stops</span>
                            <svg class="transition-all duration-200 ease-in-out"
                                :class="showStops ? 'rotate-0' : 'rotate-180'" width="10" height="7" viewBox="0 0 10 7"
                                fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M8.93202 6.66663C9.64802 6.66663 10.0307 5.82329 9.55869 5.28463L5.87802 1.07796C5.76852 0.952816 5.63353 0.852527 5.48211 0.783815C5.33068 0.715103 5.16631 0.679555 5.00002 0.679555C4.83374 0.679555 4.66937 0.715103 4.51794 0.783814C4.36651 0.852527 4.23153 0.952816 4.12202 1.07796L0.44069 5.28463C-0.0306434 5.82329 0.352023 6.66663 1.06736 6.66663L8.93269 6.66663L8.93202 6.66663Z"
                                    fill="#10182C" />
                            </svg>
                        </div>
                        <div class="overflow-hidden transition-all duration-200 ease-in-out"
                            :class="showStops ? 'max-h-[777px]' : 'max-h-0'">
                            <div class="flex py-[6px] items-center pt-[12px]">
                                <input id="any" value="any" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="stops" />
                                <label for="any" class="font-medium text-gray-900">Any</label>
                            </div>
                            <div class="flex py-[6px] items-center mt-[12px]">
                                <input id="non-stop" value="non-stop" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="stops" />
                                <label for="non-stop" class="font-medium text-gray-900">Non-stop (Direct)</label>
                            </div>
                            <div class="flex py-[6px] items-center mt-[12px]">
                                <input id="up-to-1" value="up-to-1" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="stops" />
                                <label for="up-to-1" class="font-medium text-gray-900">Up to 1 stop</label>
                            </div>
                            <div class="flex py-[6px] items-center mt-[12px]">
                                <input id="up-to-2" value="up-to-2" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="stops" />
                                <label for="up-to-2" class="font-medium text-gray-900">Up to 1 stop</label>
                            </div>
                        </div>
                    </div>
                    <div class="mt-[24px] max-w-[200px]">
                        <div class="flex items-center justify-between pb-2 border-b border-[#10182C33]"
                            @click="showAirlines = !showAirlines">
                            <span class="text-[16px] leading-[19px] font-medium">Airlines</span>
                            <svg class="transition-all duration-200 ease-in-out"
                                :class="showAirlines ? 'rotate-0' : 'rotate-180'" width="10" height="7" viewBox="0 0 10 7"
                                fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M8.93202 6.66663C9.64802 6.66663 10.0307 5.82329 9.55869 5.28463L5.87802 1.07796C5.76852 0.952816 5.63353 0.852527 5.48211 0.783815C5.33068 0.715103 5.16631 0.679555 5.00002 0.679555C4.83374 0.679555 4.66937 0.715103 4.51794 0.783814C4.36651 0.852527 4.23153 0.952816 4.12202 1.07796L0.44069 5.28463C-0.0306434 5.82329 0.352023 6.66663 1.06736 6.66663L8.93269 6.66663L8.93202 6.66663Z"
                                    fill="#10182C" />
                            </svg>
                        </div>
                        <div class="overflow-hidden transition-all duration-200 ease-in-out"
                            :class="showAirlines ? 'max-h-[777px]' : 'max-h-0'">
                            <div class="flex py-[6px] items-center pt-[12px]">
                                <input id="Areo Airlines" value="Areo Airlines" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="airlines" />
                                <label for="Areo Airlines" class="font-medium text-gray-900">Areo Airlines</label>
                            </div>
                            <div class="flex py-[6px] items-center mt-[12px]">
                                <input id="Arik Air" value="Arik Air" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="airlines" />
                                <label for="Arik Air" class="font-medium text-gray-900">Arik Air</label>
                            </div>
                            <div class="flex py-[6px] items-center mt-[12px]">
                                <input id="Dana Airlines" value="Dana Airlines" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="airlines" />
                                <label for="Dana Airlines" class="font-medium text-gray-900">Dana Airlines</label>
                            </div>
                            <div class="flex py-[6px] items-center mt-[12px]">
                                <input id="Dana Airlines" value="Dana Airlines" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="airlines" />
                                <label for="Dana Airlines" class="font-medium text-gray-900">Dana Airlines</label>
                            </div>
                        </div>
                    </div>
                    <div class="mt-[24px] max-w-[200px]">
                        <div class="flex items-center justify-between pb-2 border-b border-[#10182C33]"
                            @click="showCabin = !showCabin">
                            <span class="text-[16px] leading-[19px] font-medium">Cabin</span>
                            <svg class="transition-all duration-200 ease-in-out"
                                :class="showCabin ? 'rotate-0' : 'rotate-180'" width="10" height="7" viewBox="0 0 10 7"
                                fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M8.93202 6.66663C9.64802 6.66663 10.0307 5.82329 9.55869 5.28463L5.87802 1.07796C5.76852 0.952816 5.63353 0.852527 5.48211 0.783815C5.33068 0.715103 5.16631 0.679555 5.00002 0.679555C4.83374 0.679555 4.66937 0.715103 4.51794 0.783814C4.36651 0.852527 4.23153 0.952816 4.12202 1.07796L0.44069 5.28463C-0.0306434 5.82329 0.352023 6.66663 1.06736 6.66663L8.93269 6.66663L8.93202 6.66663Z"
                                    fill="#10182C" />
                            </svg>
                        </div>
                        <div class="overflow-hidden transition-all duration-200 ease-in-out"
                            :class="showCabin ? 'max-h-[777px]' : 'max-h-0'">
                            <div class="flex py-[6px] items-center pt-[12px]">
                                <input id="Economy Discount" value="Economy Discount" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="cabin" />
                                <label for="Economy Discount" class="font-medium text-gray-900">Economy Discount</label>
                            </div>
                            <div class="flex py-[6px] items-center pt-[12px]">
                                <input id="Economy" value="Economy" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="cabin" />
                                <label for="Economy" class="font-medium text-gray-900">Economy</label>
                            </div>
                            <div class="flex py-[6px] items-center pt-[12px]">
                                <input id="Economy Premium" value="Economy Premium" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="cabin" />
                                <label for="Economy Premium" class="font-medium text-gray-900">Economy Premium</label>
                            </div>
                            <div class="flex py-[6px] items-center pt-[12px]">
                                <input id="Business" value="Business" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="cabin" />
                                <label for="Business" class="font-medium text-gray-900">Business</label>
                            </div>
                            <div class="flex py-[6px] items-center pt-[12px]">
                                <input id="First Class" value="First Class" type="checkbox"
                                    class="h-4 w-4 rounded border-gray-300 text-indigo-600 mr-[10px]" v-model="cabin" />
                                <label for="First Class" class="font-medium text-gray-900">First Class</label>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="w-full">
                    <div class="flex items-center justify-between">
                        <span class="text-[14px] leading-[17px] font-semibold">56 results</span>
                        <div class="mr-[4px] relative" ref="sortMenu">
                            <button @click="showSortMenu = !showSortMenu"
                                class="px-[12px] py-[10px] border border-of-dark rounded-[40px] mr-[16px] flex items-center">
                                <span class="text-[14px] leading-[16px] font-medium capitalize mr-[4px]">Sort by: {{
                                    sortQuery }}</span>
                                <svg width="10" height="7" viewBox="0 0 10 7" fill="none"
                                    xmlns="http://www.w3.org/2000/svg">
                                    <path
                                        d="M1.06798 0.333374C0.351977 0.333374 -0.0306894 1.17671 0.441311 1.71537L4.12198 5.92204C4.23148 6.04718 4.36647 6.14747 4.5179 6.21619C4.66932 6.2849 4.83369 6.32044 4.99998 6.32044C5.16626 6.32044 5.33063 6.2849 5.48206 6.21619C5.63349 6.14747 5.76848 6.04718 5.87798 5.92204L9.55931 1.71537C10.0306 1.17671 9.64798 0.333374 8.93264 0.333374H1.06731H1.06798Z"
                                        fill="#10182C" />
                                </svg>

                            </button>
                            <transition name="menu">
                                <div class="absolute top-[50px] left-0 w-full z-[5]" v-if="showSortMenu">
                                    <ul class="bg-white border rounded-b-md">
                                        <li class="px-2 py-2 cursor-pointer hover:bg-of-blue hover:text-white capitalize text-base font-medium"
                                            v-for="val in sortOptions" :key="val" @click="selectSortVal(val)">
                                            {{ val }}
                                        </li>
                                    </ul>
                                </div>
                            </transition>
                        </div>
                    </div>
                    <div class="mt-[16px]">
                        <div class="bg-white rounded-[20px] border border-of-gray p-4 mb-[12px]" v-for="n in 4" :key="n">
                            <div class="flex">
                                <div class="border-r-2 border-dashed border-of-main ">
                                    <div
                                        class="flex items-center justify-between pb-[14px] border-b-2 border-dashed border-of-main pr-4">
                                        <h4 class="text-[18px] leading-[19px] font-pp">Areo Airlines</h4>
                                        <img src="https://firebasestorage.googleapis.com/v0/b/projects-1a55a.appspot.com/o/oyafly%2Fairline-logo%2Fair-peace.png?alt=media&token=378c6d75-683c-4fa9-ba17-ee7d0805f8a8"
                                            alt="" class="">
                                    </div>
                                    <div class="flex border-b-2 border-dashed border-of-main">
                                        <div class="py-[32px] px-[24px] border-r-2 border-dashed border-of-main">
                                            <h3 class="text-[14px] leading-[17px]">Lagos</h3>
                                            <h3
                                                class="text-[12px] leading-[14px] font-medium mt-[10px] max-w-[128px] truncate">
                                                Muritala Muhammad Airport 2</h3>
                                        </div>
                                        <div
                                            class="pt-[12px] pb-[32px] px-[24px] flex flex-col items-center border-r-2 border-dashed border-of-main w-full">
                                            <h3 class="text-[12px] leading-[15px] font-medium">Direct</h3>
                                            <div class="flex items-center justify-between">
                                                <span class="text-[14px] leading-[17px] font-semibold">6:30am</span>
                                                <svg class="mx-[16px]" width="161" height="32" viewBox="0 0 161 32"
                                                    fill="none" xmlns="http://www.w3.org/2000/svg">
                                                    <path d="M0.5 16H160.5" stroke="#10182C" stroke-dasharray="2 2" />
                                                    <rect width="32" height="32" transform="translate(65)" fill="white" />
                                                    <path
                                                        d="M89.3242 15.955C89.3242 16.177 89.2796 16.3967 89.1932 16.6012C89.1067 16.8057 88.98 16.9907 88.8207 17.1454C88.6614 17.3 88.4727 17.4211 88.2657 17.5015C88.0588 17.5818 87.8378 17.6199 87.6159 17.6133L83.6676 17.4975L80.7892 23.45C80.5584 23.9283 80.0726 24.2333 79.5409 24.2333C79.4317 24.2334 79.3237 24.2103 79.2241 24.1655C79.1245 24.1208 79.0356 24.0554 78.9631 23.9737C78.8906 23.8921 78.8363 23.7959 78.8038 23.6917C78.7712 23.5875 78.7611 23.4775 78.7742 23.3691L79.4934 17.375L76.3559 17.2833L75.9476 18.4008C75.8719 18.6077 75.7346 18.7863 75.5541 18.9125C75.3736 19.0388 75.1587 19.1065 74.9384 19.1066C74.8397 19.1066 74.742 19.0872 74.6509 19.0494C74.5597 19.0116 74.4769 18.9562 74.4072 18.8864C74.3374 18.8166 74.2822 18.7337 74.2445 18.6425C74.2068 18.5514 74.1874 18.4536 74.1876 18.355V17.125L73.5126 16.9841C73.2761 16.9349 73.0639 16.8057 72.9116 16.6183C72.7592 16.431 72.676 16.1969 72.676 15.9554C72.676 15.7139 72.7592 15.4798 72.9116 15.2924C73.0639 15.105 73.2761 14.9759 73.5126 14.9266L74.1876 14.7866V13.555C74.1874 13.3721 74.254 13.1954 74.3749 13.0582C74.4959 12.921 74.6628 12.8327 74.8442 12.81L74.9384 12.8041C75.1584 12.8043 75.3731 12.872 75.5534 12.9981C75.7337 13.1242 75.871 13.3025 75.9467 13.5091L76.3567 14.6258L79.4826 14.5341L78.7742 8.63079C78.7727 8.61555 78.7716 8.60026 78.7709 8.58496L78.7692 8.53912C78.7692 8.11329 79.1151 7.76746 79.5409 7.76746C80.0284 7.76746 80.4767 8.02329 80.7267 8.43412L80.7892 8.55079L83.6251 14.4133L87.6167 14.2966C88.0565 14.2838 88.4834 14.4463 88.8035 14.7482C89.1235 15.0501 89.3105 15.4668 89.3234 15.9066L89.3242 15.955Z"
                                                        fill="#10182C" />
                                                </svg>
                                                <span class="text-[14px] leading-[17px] font-semibold">6:30am</span>
                                            </div>
                                            <div class="flex items-center">
                                                <svg class="mr-[4px]" width="12" height="14" viewBox="0 0 12 14" fill="none"
                                                    xmlns="http://www.w3.org/2000/svg">
                                                    <path
                                                        d="M6.00004 1.83329C7.50293 1.83329 8.94427 2.43032 10.007 3.49302C11.0697 4.55573 11.6667 5.99707 11.6667 7.49996C11.6667 9.00285 11.0697 10.4442 10.007 11.5069C8.94427 12.5696 7.50293 13.1666 6.00004 13.1666C4.49715 13.1666 3.05581 12.5696 1.9931 11.5069C0.930396 10.4442 0.333374 9.00285 0.333374 7.49996C0.333374 5.99707 0.930396 4.55573 1.9931 3.49302C3.05581 2.43032 4.49715 1.83329 6.00004 1.83329ZM6.00004 3.83329C5.87922 3.8333 5.76248 3.87705 5.67142 3.95647C5.58036 4.03589 5.52114 4.14559 5.50471 4.26529L5.50004 4.33329V7.33329L5.50471 7.40129C5.52117 7.52097 5.58041 7.63063 5.67147 7.71002C5.76252 7.7894 5.87924 7.83314 6.00004 7.83314C6.12084 7.83314 6.23756 7.7894 6.32862 7.71002C6.41967 7.63063 6.47891 7.52097 6.49537 7.40129L6.50004 7.33329V4.33329L6.49537 4.26529C6.47894 4.14559 6.41972 4.03589 6.32866 3.95647C6.2376 3.87705 6.12087 3.8333 6.00004 3.83329ZM10.78 1.91529L10.8347 1.95596L11.6007 2.62263C11.6967 2.70574 11.7575 2.82226 11.7707 2.94854C11.7839 3.07482 11.7486 3.20141 11.6719 3.30261C11.5953 3.40381 11.4829 3.47204 11.3578 3.49347C11.2326 3.51489 11.104 3.48789 10.998 3.41796L10.944 3.37729L10.178 2.71063C10.0829 2.62734 10.0228 2.51108 10.0099 2.38527C9.99707 2.25947 10.0323 2.13346 10.1087 2.03262C10.185 1.93179 10.2967 1.86362 10.4213 1.84185C10.5458 1.82008 10.674 1.84632 10.78 1.91529ZM7.50004 0.166626C7.62672 0.166665 7.74867 0.214789 7.84124 0.301274C7.9338 0.38776 7.99009 0.506158 7.99872 0.632546C8.00736 0.758934 7.9677 0.883887 7.88775 0.982159C7.80781 1.08043 7.69354 1.14469 7.56804 1.16196L7.50004 1.16663H4.50004C4.37336 1.16659 4.25141 1.11846 4.15885 1.03198C4.06628 0.945492 4.00999 0.827094 4.00136 0.700706C3.99272 0.574318 4.03238 0.449365 4.11233 0.351093C4.19227 0.252822 4.30654 0.18856 4.43204 0.171293L4.50004 0.166626H7.50004Z"
                                                        fill="#10182C" />
                                                </svg>
                                                <span class="text-[12px] leading-[15px] font-medium">1hr 10m</span>
                                            </div>
                                        </div>
                                        <div class="py-[32px] px-[24px]">
                                            <h3 class="text-[14px] leading-[17px]">Abuja</h3>
                                            <h3
                                                class="text-[12px] leading-[14px] font-medium mt-[10px] max-w-[128px] truncate">
                                                Dr Nnamdi Azikwe Airport</h3>
                                        </div>
                                    </div>
                                    <div class="flex border-b-2 border-dashed border-of-main">
                                        <div class="py-[32px] px-[24px] border-r-2 border-dashed border-of-main">
                                            <h3 class="text-[14px] leading-[17px]">Abuja</h3>
                                            <h3
                                                class="text-[12px] leading-[14px] font-medium mt-[10px] max-w-[128px] truncate">
                                                Dr Nnamdi Azikwe Airport</h3>
                                        </div>
                                        <div
                                            class="pt-[12px] pb-[32px] px-[24px] flex flex-col items-center border-r-2 border-dashed border-of-main w-full">
                                            <h3 class="text-[12px] leading-[15px] font-medium">Direct</h3>
                                            <div class="flex items-center justify-between">
                                                <span class="text-[14px] leading-[17px] font-semibold">2:30am</span>
                                                <svg class="mx-[16px]" width="161" height="32" viewBox="0 0 161 32"
                                                    fill="none" xmlns="http://www.w3.org/2000/svg">
                                                    <path d="M0.5 16H160.5" stroke="#10182C" stroke-dasharray="2 2" />
                                                    <rect width="32" height="32" transform="translate(65)" fill="white" />
                                                    <path
                                                        d="M89.3242 15.955C89.3242 16.177 89.2796 16.3967 89.1932 16.6012C89.1067 16.8057 88.98 16.9907 88.8207 17.1454C88.6614 17.3 88.4727 17.4211 88.2657 17.5015C88.0588 17.5818 87.8378 17.6199 87.6159 17.6133L83.6676 17.4975L80.7892 23.45C80.5584 23.9283 80.0726 24.2333 79.5409 24.2333C79.4317 24.2334 79.3237 24.2103 79.2241 24.1655C79.1245 24.1208 79.0356 24.0554 78.9631 23.9737C78.8906 23.8921 78.8363 23.7959 78.8038 23.6917C78.7712 23.5875 78.7611 23.4775 78.7742 23.3691L79.4934 17.375L76.3559 17.2833L75.9476 18.4008C75.8719 18.6077 75.7346 18.7863 75.5541 18.9125C75.3736 19.0388 75.1587 19.1065 74.9384 19.1066C74.8397 19.1066 74.742 19.0872 74.6509 19.0494C74.5597 19.0116 74.4769 18.9562 74.4072 18.8864C74.3374 18.8166 74.2822 18.7337 74.2445 18.6425C74.2068 18.5514 74.1874 18.4536 74.1876 18.355V17.125L73.5126 16.9841C73.2761 16.9349 73.0639 16.8057 72.9116 16.6183C72.7592 16.431 72.676 16.1969 72.676 15.9554C72.676 15.7139 72.7592 15.4798 72.9116 15.2924C73.0639 15.105 73.2761 14.9759 73.5126 14.9266L74.1876 14.7866V13.555C74.1874 13.3721 74.254 13.1954 74.3749 13.0582C74.4959 12.921 74.6628 12.8327 74.8442 12.81L74.9384 12.8041C75.1584 12.8043 75.3731 12.872 75.5534 12.9981C75.7337 13.1242 75.871 13.3025 75.9467 13.5091L76.3567 14.6258L79.4826 14.5341L78.7742 8.63079C78.7727 8.61555 78.7716 8.60026 78.7709 8.58496L78.7692 8.53912C78.7692 8.11329 79.1151 7.76746 79.5409 7.76746C80.0284 7.76746 80.4767 8.02329 80.7267 8.43412L80.7892 8.55079L83.6251 14.4133L87.6167 14.2966C88.0565 14.2838 88.4834 14.4463 88.8035 14.7482C89.1235 15.0501 89.3105 15.4668 89.3234 15.9066L89.3242 15.955Z"
                                                        fill="#10182C" />
                                                </svg>
                                                <span class="text-[14px] leading-[17px] font-semibold">3:55am</span>
                                            </div>
                                            <div class="flex items-center">
                                                <svg class="mr-[4px]" width="12" height="14" viewBox="0 0 12 14" fill="none"
                                                    xmlns="http://www.w3.org/2000/svg">
                                                    <path
                                                        d="M6.00004 1.83329C7.50293 1.83329 8.94427 2.43032 10.007 3.49302C11.0697 4.55573 11.6667 5.99707 11.6667 7.49996C11.6667 9.00285 11.0697 10.4442 10.007 11.5069C8.94427 12.5696 7.50293 13.1666 6.00004 13.1666C4.49715 13.1666 3.05581 12.5696 1.9931 11.5069C0.930396 10.4442 0.333374 9.00285 0.333374 7.49996C0.333374 5.99707 0.930396 4.55573 1.9931 3.49302C3.05581 2.43032 4.49715 1.83329 6.00004 1.83329ZM6.00004 3.83329C5.87922 3.8333 5.76248 3.87705 5.67142 3.95647C5.58036 4.03589 5.52114 4.14559 5.50471 4.26529L5.50004 4.33329V7.33329L5.50471 7.40129C5.52117 7.52097 5.58041 7.63063 5.67147 7.71002C5.76252 7.7894 5.87924 7.83314 6.00004 7.83314C6.12084 7.83314 6.23756 7.7894 6.32862 7.71002C6.41967 7.63063 6.47891 7.52097 6.49537 7.40129L6.50004 7.33329V4.33329L6.49537 4.26529C6.47894 4.14559 6.41972 4.03589 6.32866 3.95647C6.2376 3.87705 6.12087 3.8333 6.00004 3.83329ZM10.78 1.91529L10.8347 1.95596L11.6007 2.62263C11.6967 2.70574 11.7575 2.82226 11.7707 2.94854C11.7839 3.07482 11.7486 3.20141 11.6719 3.30261C11.5953 3.40381 11.4829 3.47204 11.3578 3.49347C11.2326 3.51489 11.104 3.48789 10.998 3.41796L10.944 3.37729L10.178 2.71063C10.0829 2.62734 10.0228 2.51108 10.0099 2.38527C9.99707 2.25947 10.0323 2.13346 10.1087 2.03262C10.185 1.93179 10.2967 1.86362 10.4213 1.84185C10.5458 1.82008 10.674 1.84632 10.78 1.91529ZM7.50004 0.166626C7.62672 0.166665 7.74867 0.214789 7.84124 0.301274C7.9338 0.38776 7.99009 0.506158 7.99872 0.632546C8.00736 0.758934 7.9677 0.883887 7.88775 0.982159C7.80781 1.08043 7.69354 1.14469 7.56804 1.16196L7.50004 1.16663H4.50004C4.37336 1.16659 4.25141 1.11846 4.15885 1.03198C4.06628 0.945492 4.00999 0.827094 4.00136 0.700706C3.99272 0.574318 4.03238 0.449365 4.11233 0.351093C4.19227 0.252822 4.30654 0.18856 4.43204 0.171293L4.50004 0.166626H7.50004Z"
                                                        fill="#10182C" />
                                                </svg>
                                                <span class="text-[12px] leading-[15px] font-medium">1hr 10m</span>
                                            </div>
                                        </div>
                                        <div class="py-[32px] px-[24px]">
                                            <h3 class="text-[14px] leading-[17px]">Lagos</h3>
                                            <h3
                                                class="text-[12px] leading-[14px] font-medium mt-[10px] max-w-[128px] truncate">
                                                Muritala Muhammad Airport 2</h3>
                                        </div>
                                    </div>
                                </div>
                                <div class="flex flex-col justify-end w-[250px]">
                                    <div class="pb-[12px] pl-[16px] border-b-2 border-dashed border-of-main">
                                        <div class="flex items-center">
                                            <svg class="mr-[4px]" width="14" height="15" viewBox="0 0 14 15" fill="none"
                                                xmlns="http://www.w3.org/2000/svg">
                                                <path
                                                    d="M9.39333 1.18669C9.11205 0.905589 8.73066 0.747681 8.33299 0.747681C7.93533 0.747681 7.55394 0.905589 7.27266 1.18669L0.686661 7.77336C0.547371 7.91265 0.43688 8.07801 0.361497 8.26C0.286114 8.44199 0.247314 8.63704 0.247314 8.83403C0.247314 9.03101 0.286114 9.22607 0.361497 9.40806C0.43688 9.59005 0.547371 9.75541 0.686661 9.89469L1.46799 10.6754C1.80799 11.016 2.28599 10.9554 2.57466 10.7834C2.7339 10.6888 2.92009 10.65 3.10384 10.673C3.28759 10.6961 3.45843 10.7797 3.58938 10.9106C3.72033 11.0416 3.80393 11.2124 3.82698 11.3962C3.85003 11.5799 3.81121 11.7661 3.71666 11.9254C3.54533 12.214 3.48399 12.692 3.82466 13.032L4.60666 13.8134C4.74595 13.9526 4.91131 14.0631 5.0933 14.1385C5.27529 14.2139 5.47034 14.2527 5.66733 14.2527C5.86431 14.2527 6.05937 14.2139 6.24136 14.1385C6.42335 14.0631 6.58871 13.9526 6.72799 13.8134L13.3133 7.22803C13.4526 7.08874 13.5631 6.92338 13.6385 6.74139C13.7139 6.5594 13.7527 6.36435 13.7527 6.16736C13.7527 5.97038 13.7139 5.77532 13.6385 5.59333C13.5631 5.41134 13.4526 5.24598 13.3133 5.10669L12.5327 4.32536C12.1927 3.98536 11.714 4.04536 11.4253 4.21736C11.2661 4.31191 11.0799 4.35073 10.8961 4.32768C10.7124 4.30463 10.5416 4.22103 10.4106 4.09008C10.2797 3.95913 10.1961 3.78829 10.173 3.60454C10.15 3.42079 10.1888 3.2346 10.2833 3.07536C10.4553 2.78669 10.516 2.30869 10.1753 1.96869L9.39333 1.18669Z"
                                                    fill="#10182C" />
                                            </svg>
                                            <span class="text-[12px] leading-[15px] font-medium">Economy.</span>
                                            <RouterLink to="/" class="text-[12px] leading-[15px] font-medium underline">
                                                Flight details</RouterLink>
                                        </div>
                                        <div class="flex items-center px-3 py-2 rounded-[20px] my-[12px] bg-[#D7E6FE80] w-full">
                                            <svg width="14" height="15" viewBox="0 0 14 15" fill="none"
                                                xmlns="http://www.w3.org/2000/svg">
                                                <path
                                                    d="M7.00004 0.832031C10.6827 0.832031 13.668 3.81736 13.668 7.50003C13.668 11.182 10.6827 14.1667 7.00004 14.1667C3.31737 14.1674 0.333374 11.182 0.333374 7.50003C0.332707 3.81736 3.31737 0.832031 7.00004 0.832031ZM6.99737 6.33203C6.834 6.33225 6.67639 6.39246 6.55447 6.50123C6.43256 6.60999 6.35483 6.75974 6.33604 6.92203L6.33137 6.99936L6.33404 10.6674L6.33804 10.7447C6.35667 10.9073 6.43447 11.0574 6.55661 11.1663C6.67875 11.2753 6.8367 11.3355 7.00037 11.3355C7.16404 11.3355 7.322 11.2753 7.44414 11.1663C7.56628 11.0574 7.64408 10.9073 7.66271 10.7447L7.66671 10.6667L7.66404 6.9987L7.65937 6.9207C7.6401 6.75854 7.56199 6.60909 7.43984 6.5007C7.31769 6.39232 7.16001 6.33254 6.99671 6.3327L6.99737 6.33203ZM7.00071 3.8327C6.77943 3.8327 6.56721 3.9206 6.41074 4.07707C6.25428 4.23354 6.16637 4.44575 6.16637 4.66703C6.16637 4.88831 6.25428 5.10053 6.41074 5.25699C6.56721 5.41346 6.77943 5.50136 7.00071 5.50136C7.11023 5.50132 7.21867 5.47971 7.31984 5.43775C7.42101 5.3958 7.51292 5.33433 7.59034 5.25686C7.66775 5.17938 7.72915 5.08742 7.77102 4.98621C7.81289 4.88501 7.83442 4.77655 7.83437 4.66703C7.83433 4.55751 7.81272 4.44907 7.77076 4.3479C7.72881 4.24673 7.66734 4.15481 7.58987 4.0774C7.51239 3.99999 7.42043 3.93859 7.31922 3.89672C7.21802 3.85485 7.10956 3.83332 7.00004 3.83336L7.00071 3.8327Z"
                                                    fill="#10182C" />
                                            </svg>
                                            <span class="ml-[5px] text-[14px] leading-[16px] font-semibold">
                                                Discount valid until 18 Oct
                                            </span>
                                        </div>
                                    </div>
                                    <div class="px-[16px] pt-[16px]">
                                        <div class="flex items-end mb-[22px]">
                                            <span class="text-[20px] leading-[21px] font-pp mr-2">₦200,000</span>
                                            <span
                                                class="text-[16px] leading-[16px] line-through font-pp font-semibold">₦536,000</span>
                                        </div>
                                        <button class="rounded-xl p-2 bg-of-blue flex items-center justify-center w-full">
                                            <span class="text-[14px] leading-normal font-semibold text-white">Book flight</span>
                                            <svg class="ml-1" xmlns="http://www.w3.org/2000/svg" width="16" height="16"
                                                viewBox="0 0 16 16" fill="none">
                                                <path
                                                    d="M9.136 2.85599C9.07437 2.79139 9.00039 2.73983 8.91845 2.70437C8.83651 2.66891 8.74829 2.65027 8.65901 2.64956C8.56973 2.64884 8.48122 2.66607 8.39873 2.70021C8.31623 2.73435 8.24143 2.78471 8.17877 2.84831C8.11611 2.91191 8.06687 2.98745 8.03395 3.07044C8.00104 3.15343 7.98513 3.24219 7.98717 3.33145C7.98922 3.42071 8.00917 3.50865 8.04584 3.59005C8.08251 3.67145 8.13516 3.74465 8.20067 3.80532L11.78 7.33332H2.66667C2.48986 7.33332 2.32029 7.40356 2.19526 7.52858C2.07024 7.65361 2 7.82317 2 7.99999C2 8.1768 2.07024 8.34637 2.19526 8.47139C2.32029 8.59641 2.48986 8.66665 2.66667 8.66665H11.7767L8.2 12.19C8.0804 12.3153 8.0143 12.4823 8.01569 12.6555C8.01708 12.8288 8.08585 12.9947 8.20744 13.1181C8.32903 13.2415 8.49389 13.3127 8.66709 13.3167C8.84029 13.3207 9.00823 13.257 9.13533 13.1393L13.752 8.59132C13.8306 8.51379 13.893 8.42142 13.9356 8.31956C13.9782 8.2177 14.0002 8.10839 14.0002 7.99799C14.0002 7.88758 13.9782 7.77827 13.9356 7.67641C13.893 7.57455 13.8306 7.48218 13.752 7.40465L9.13533 2.85599H9.136Z"
                                                    fill="white" />
                                            </svg>
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>
        <Footer />
    </main></template>
