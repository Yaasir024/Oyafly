<script setup>
import { ref, onMounted, computed, shallowRef, h } from 'vue';
import { useRoute, useRouter } from 'vue-router';

import { ElDatePicker } from 'element-plus'
import 'element-plus/dist/index.css'

import axios from 'axios';
import { useClickOutside } from "@/composables/useClickOutside";

const route = useRoute()
const router = useRouter()

const value1 = ref('')

const customPrefix = shallowRef({
    render() {
        return h('p', 'pre')
    },
})

const airport = ref({
    from: {},
    to: {},
    time: ''
})
const value = ref('')
const defaultTime = ref < [Date, Date] > ([
    new Date(2000, 1, 1, 0, 0, 0),
    new Date(2000, 2, 1, 23, 59, 59),
])


onMounted(() => {
    if (route.path == '/search') {
        airport.value = { "from": { "code": "LOS", "city": "Lagos", "fullName": "Murtala Muhammed Airport" }, "to": { "code": "ABV", "city": "Abuja", "fullName": "Abuja Nnamdi Azikiwe International Airport" }, "time": ["2023-07-18T23:00:00.000Z", "2023-07-29T23:00:00.000Z"] }
    }
})



const airports = [
    {
        code: "LOS",
        city: "Lagos",
        fullName: "Murtala Muhammed Airport",
    },
    {
        code: "ABV",
        city: "Abuja",
        fullName: "Abuja Nnamdi Azikiwe International Airport",
    },
    {
        code: "KAN",
        city: "Kano",
        fullName: "Mallam Aminu Kano International Airport",
    },
]

const toMenu = ref(null)
const showToMenu = ref(false)

useClickOutside(toMenu, () => {
    showToMenu.value = false;
});
const fromMenu = ref(null)
const showFromMenu = ref(false)

useClickOutside(fromMenu, () => {
    showFromMenu.value = false;
});


const toQuery = ref("")
const fromQuery = ref("")
const filteredToData = computed(() => {
    const query = ref(toQuery.value.toLowerCase());
    if (toQuery.value === "") {
        return airports;
    }
    return airports.filter((item) => {
        return Object.values(item).some((word) =>
            String(word).toLowerCase().includes(query.value)
        );
    });
});
const filteredFromData = computed(() => {
    const query = ref(fromQuery.value.toLowerCase());
    if (fromQuery.value === "") {
        return airports;
    }
    return airports.filter((item) => {
        return Object.values(item).some((word) =>
            String(word).toLowerCase().includes(query.value)
        );
    });
});

// select for from 
const selectFromAirport = (c) => {
    console.log(c)
    airport.value.from = c
    showFromMenu.value = false
}
// Select for to
const selectToAirport = (c) => {
    console.log(c)
    airport.value.to = c
    showToMenu.value = false
}
// Switch two airports
const switchAirports = () => {
    let newFrom = airport.value.to
    let newTo = airport.value.from

    airport.value.from = newFrom
    airport.value.to = newTo
}

const datePicker = ref(null)
const openDateTime = () => {
    datePicker.value.dispatchEvent(new Event('click'))
    console.log('click', datePicker.value)
}

const search = () => {
    router.push('/search')
}
</script>

<template>
    <div class="bg-white rounded-[20px] p-[6px] mt-2 flex flex-col xl:flex-row">
        <div
            class="flex flex-full xl:flex-75% flex-col md:flex-row md:items-center border-2 border-[#D7E6FE] bg-[#F3F7FF] rounded-[14px] flex-wrap md:flex-nowrap">
            <div class="h-[75px] md:h-[84px] flex items-center px-[12px] xl:px-[19px] border-b md:border-b-0 border-r-0 md:border-r border-[#D7E6FE] md:flex-33.33%  relative"
                ref="fromMenu">
                <div class="flex items-center h-full cursor-pointer" @click="showFromMenu = !showFromMenu">
                    <svg class="mr-[12px]" width="20" height="17" viewBox="0 0 20 17" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M7.523 0.41L9.393 1.925C9.203 2.13 9.036 2.323 8.895 2.492C8.771 2.642 8.657 2.69 8.601 2.702L5.138 3.424L4.756 2.742C4.068 1.514 4.956 0 6.363 0C6.785 0 7.195 0.145 7.523 0.41ZM13.693 0.503C15.93 0.33 17.602 1.746 18.547 2.829C19.036 3.389 19.134 4.097 18.925 4.712C18.8167 5.01973 18.6394 5.29862 18.4068 5.5274C18.1743 5.75617 17.8925 5.92876 17.583 6.032L12.212 7.884L8.976 12.199C8.68333 12.5892 8.25839 12.8593 7.78084 12.9586C7.30329 13.0579 6.80591 12.9796 6.38194 12.7384C5.95798 12.4972 5.63652 12.1097 5.47785 11.6485C5.31917 11.1872 5.33416 10.684 5.52 10.233L6.028 9L2.727 9.635C2.39511 9.69879 2.05322 9.68846 1.72578 9.60475C1.39834 9.52103 1.09344 9.366 0.832894 9.15074C0.572344 8.93548 0.362577 8.6653 0.218593 8.35954C0.0746091 8.05377 -3.43408e-05 7.71997 3.84399e-07 7.382V3.692C-0.00025301 3.31606 0.124778 2.95075 0.355335 2.65381C0.585891 2.35686 0.908827 2.14522 1.27311 2.05231C1.63739 1.9594 2.02224 1.99054 2.36685 2.14079C2.71146 2.29105 2.99618 2.55186 3.176 2.882L4.142 4.652L8.805 3.682C9.119 3.616 9.422 3.422 9.665 3.131C10.035 2.684 10.594 2.076 11.263 1.56C11.923 1.052 12.763 0.574 13.693 0.503ZM0.75 15.5C0.551088 15.5 0.360322 15.579 0.21967 15.7197C0.0790179 15.8603 3.84399e-07 16.0511 3.84399e-07 16.25C3.84399e-07 16.4489 0.0790179 16.6397 0.21967 16.7803C0.360322 16.921 0.551088 17 0.75 17H17.25C17.4489 17 17.6397 16.921 17.7803 16.7803C17.921 16.6397 18 16.4489 18 16.25C18 16.0511 17.921 15.8603 17.7803 15.7197C17.6397 15.579 17.4489 15.5 17.25 15.5H0.75Z"
                            fill="#10182C" />
                    </svg>
                    <span class="text-base xl:text-lg leading-[22px]" v-if="airport.from.code">({{ airport.from.code
                    }})</span>
                    <input type="text" placeholder="From?" v-model="airport.from.fullName"
                        class="placeholder:text-of-dark text-base xl:text-lg leading-[22px] w-full outline-none bg-transparent cursor-pointer"
                        readonly>
                </div>
                <transition name="menu">
                    <div class="absolute top-[60px] left-0 z-[5] w-full bg-white border rounded-b-md shadow-md"
                        v-if="showFromMenu">
                        <ul class="">
                            <div class="px-2 py-3 border-b">
                                <input type="text" placeholder="Search..."
                                    class="border-2 w-full p-1 outline-none rounded-md" v-model="fromQuery">
                            </div>
                            <div class="" v-if="filteredFromData.length != 0">
                                <li class="px-2 py-2 cursor-pointer hover:bg-of-blue hover:text-white capitalize text-base font-medium border-b"
                                    v-for="airport in filteredFromData" :key="airport" @click="selectFromAirport(airport)">
                                    <div class="flex items-center justify-between">
                                        <span class="text-base font-medium">
                                            {{ airport.city }}
                                        </span>
                                        <span class="text-base font-medium">
                                            {{ airport.code }}
                                        </span>
                                    </div>
                                    <p class="text-[13px] mt-2">
                                        {{ airport.fullName }}
                                    </p>
                                </li>
                            </div>
                            <div class="py-4 flex items-center justify-center" v-else>
                                <span class="text-[20px] font-semibold">
                                    No results
                                </span>
                            </div>
                        </ul>
                    </div>
                </transition>
                <button @click="switchAirports"
                    class="absolute bottom-[-25px] md:bottom-[50%] md:translate-y-[50%] right-[50%] md:right-[-25px] z-[4] h-[48px] w-[48px] rounded-full bg-white flex items-center justify-center border border-of-gray rotate-90 md:rotate-0">
                    <svg width="18" height="22" viewBox="0 0 18 22" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M0.997681 5.75272L1.00468 5.85272C1.02889 6.03264 1.11753 6.19767 1.25416 6.3172C1.39079 6.43673 1.56614 6.50265 1.74768 6.50272L14.4397 6.50272L11.2217 9.72272L11.1497 9.80672C11.0365 9.95892 10.9853 10.1483 11.0062 10.3368C11.0271 10.5253 11.1186 10.6989 11.2624 10.8226C11.4061 10.9463 11.5914 11.011 11.7809 11.0036C11.9704 10.9962 12.15 10.9173 12.2837 10.7827L16.7837 6.27872L16.8557 6.19472C16.9624 6.05025 17.0137 5.87228 17.0003 5.69317C16.9869 5.51406 16.9097 5.34571 16.7827 5.21872L12.2827 0.721721L12.1987 0.64972C12.0541 0.542734 11.8759 0.49125 11.6966 0.504649C11.5173 0.518049 11.3487 0.595441 11.2217 0.72272L11.1497 0.806722C11.0427 0.951272 10.9912 1.12945 11.0046 1.30879C11.018 1.48812 11.0954 1.65667 11.2227 1.78372L14.4437 5.00272L1.74768 5.00272L1.64568 5.00872C1.46613 5.03337 1.30157 5.1222 1.18245 5.25879C1.06332 5.39538 0.997688 5.57148 0.997681 5.75272ZM1.21768 16.7887L5.71268 21.2827L5.79668 21.3557C5.94115 21.4624 6.11912 21.5138 6.29823 21.5004C6.47734 21.487 6.64569 21.4097 6.77268 21.2827L6.84568 21.1987C6.95239 21.0543 7.00372 20.8763 6.99032 20.6972C6.97693 20.5181 6.8997 20.3497 6.77268 20.2227L3.55468 17.0057H16.2527L16.3547 16.9977C16.5342 16.9731 16.6988 16.8842 16.8179 16.7477C16.937 16.6111 17.0027 16.436 17.0027 16.2547L16.9957 16.1537C16.9713 15.974 16.8825 15.8092 16.7459 15.6899C16.6093 15.5705 16.4341 15.5048 16.2527 15.5047L3.55668 15.5057L6.77368 12.2827L6.84568 12.1987C6.9574 12.0464 7.00753 11.8576 6.98606 11.6699C6.96459 11.4822 6.87311 11.3096 6.72988 11.1864C6.58665 11.0633 6.40224 10.9987 6.21348 11.0056C6.02472 11.0126 5.84552 11.0904 5.71168 11.2237L1.21768 15.7277L1.14568 15.8127C1.03897 15.9572 0.987642 16.1352 1.00104 16.3143C1.01443 16.4934 1.09166 16.6617 1.21868 16.7887H1.21768Z"
                            fill="#10182C" />
                    </svg>
                </button>
            </div>
            <!-- TO -->
            <div class="h-[75px] md:h-[84px] flex items-center px-[12px] md:pr-[19px] md:pl-[38px]  md:flex-33.33% border-b md:border-b-0 border-r-0 md:border-r border-[#D7E6FE] relative"
                ref="toMenu">
                <div class="flex items-center w-full h-full cursor-pointer" @click="showToMenu = !showToMenu">
                    <svg class="mr-[12px]" width="19" height="18" viewBox="0 0 19 18" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M7.33342 2.03901V2.81701L10.3604 4.01901H12.4794L11.2294 1.21101C10.3354 -0.797993 7.33342 -0.158993 7.33342 2.03901ZM10.0534 4.97401L5.83342 3.29701V1.75701C5.83342 0.0190067 3.57442 -0.656993 2.62042 0.796007L0.710418 3.70401C0.524742 3.98705 0.403714 4.30752 0.355944 4.64264C0.308173 4.97776 0.334833 5.31929 0.434028 5.64294C0.533222 5.96659 0.702514 6.2644 0.929863 6.5152C1.15721 6.766 1.43703 6.96362 1.74942 7.09401L5.25242 8.55801L3.20742 10.456C1.58042 11.967 3.20342 14.621 5.28942 13.861L12.0504 11.397L15.5134 12.843C15.8228 12.9721 16.1592 13.0228 16.4928 12.9906C16.8264 12.9584 17.147 12.8444 17.426 12.6586C17.7049 12.4728 17.9337 12.221 18.092 11.9256C18.2503 11.6301 18.3333 11.3002 18.3334 10.965V9.73501C18.3335 9.11574 18.2117 8.50251 17.9748 7.93035C17.7379 7.35818 17.3906 6.83829 16.9528 6.40035C16.5149 5.96242 15.9951 5.61502 15.423 5.37801C14.8509 5.141 14.2377 5.01901 13.6184 5.01901H10.2924C10.211 5.0192 10.1292 5.00392 10.0534 4.97401ZM0.333418 17.25C0.333418 17.0511 0.412436 16.8603 0.553088 16.7197C0.69374 16.579 0.884506 16.5 1.08342 16.5H17.5834C17.7823 16.5 17.9731 16.579 18.1137 16.7197C18.2544 16.8603 18.3334 17.0511 18.3334 17.25C18.3334 17.4489 18.2544 17.6397 18.1137 17.7803C17.9731 17.921 17.7823 18 17.5834 18H1.08342C0.884506 18 0.69374 17.921 0.553088 17.7803C0.412436 17.6397 0.333418 17.4489 0.333418 17.25Z"
                            fill="#10182C" />
                    </svg>
                    <span class="text-base xl:text-lg leading-[22px]" v-if="airport.to.code">({{ airport.to.code }})</span>
                    <input type="text" placeholder="To?" v-model="airport.to.fullName"
                        class="placeholder:text-of-dark text-base xl:text-lg leading-[22px] w-full outline-none bg-transparent cursor-pointer"
                        readonly>
                </div>
                <transition name="menu">
                    <div class="absolute top-[60px] left-0 z-[5] w-full bg-white border rounded-b-md shadow-md"
                        v-if="showToMenu">
                        <ul class="">
                            <div class="px-2 py-3 border-b">
                                <input type="text" placeholder="Search..."
                                    class="border-2 w-full p-1 outline-none rounded-md" v-model="toQuery">
                            </div>
                            <div class="" v-if="filteredToData.length != 0">
                                <li class="px-2 py-2 cursor-pointer hover:bg-of-blue hover:text-white capitalize text-base font-medium border-b"
                                    v-for="airport in filteredToData" :key="airport" @click="selectToAirport(airport)">
                                    <div class="flex items-center justify-between">
                                        <span class="text-base font-medium">
                                            {{ airport.city }}
                                        </span>
                                        <span class="text-base font-medium">
                                            {{ airport.code }}
                                        </span>
                                    </div>
                                    <p class="text-[13px] mt-2">
                                        {{ airport.fullName }}
                                    </p>
                                </li>
                            </div>
                            <div class="py-4 flex items-center justify-center" v-else>
                                <span class="text-[20px] font-semibold">
                                    No results
                                </span>
                            </div>
                        </ul>
                    </div>
                </transition>
            </div>
            <div class="h-[75px] md:h-[84px] flex items-center px-[12px] xl:px-[19px]  md:flex-33.33%">
                <div class="flex items-center">
                    <svg class="mr-[12px]" width="19" height="18" viewBox="0 0 19 18" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M18.6667 5.5V14.75C18.6667 15.612 18.3243 16.4386 17.7148 17.0481C17.1054 17.6576 16.2787 18 15.4167 18H3.91675C3.05479 18 2.22814 17.6576 1.61865 17.0481C1.00916 16.4386 0.666748 15.612 0.666748 14.75V5.5H18.6667ZM4.91675 12C4.58523 12 4.26729 12.1317 4.03286 12.3661C3.79844 12.6005 3.66675 12.9185 3.66675 13.25C3.66675 13.5815 3.79844 13.8995 4.03286 14.1339C4.26729 14.3683 4.58523 14.5 4.91675 14.5C5.24827 14.5 5.56621 14.3683 5.80063 14.1339C6.03505 13.8995 6.16675 13.5815 6.16675 13.25C6.16675 12.9185 6.03505 12.6005 5.80063 12.3661C5.56621 12.1317 5.24827 12 4.91675 12ZM9.66675 12C9.33523 12 9.01729 12.1317 8.78286 12.3661C8.54844 12.6005 8.41675 12.9185 8.41675 13.25C8.41675 13.5815 8.54844 13.8995 8.78286 14.1339C9.01729 14.3683 9.33523 14.5 9.66675 14.5C9.99827 14.5 10.3162 14.3683 10.5506 14.1339C10.7851 13.8995 10.9167 13.5815 10.9167 13.25C10.9167 12.9185 10.7851 12.6005 10.5506 12.3661C10.3162 12.1317 9.99827 12 9.66675 12ZM4.91675 7.5C4.58523 7.5 4.26729 7.6317 4.03286 7.86612C3.79844 8.10054 3.66675 8.41848 3.66675 8.75C3.66675 9.08152 3.79844 9.39946 4.03286 9.63388C4.26729 9.8683 4.58523 10 4.91675 10C5.24827 10 5.56621 9.8683 5.80063 9.63388C6.03505 9.39946 6.16675 9.08152 6.16675 8.75C6.16675 8.41848 6.03505 8.10054 5.80063 7.86612C5.56621 7.6317 5.24827 7.5 4.91675 7.5ZM9.66675 7.5C9.33523 7.5 9.01729 7.6317 8.78286 7.86612C8.54844 8.10054 8.41675 8.41848 8.41675 8.75C8.41675 9.08152 8.54844 9.39946 8.78286 9.63388C9.01729 9.8683 9.33523 10 9.66675 10C9.99827 10 10.3162 9.8683 10.5506 9.63388C10.7851 9.39946 10.9167 9.08152 10.9167 8.75C10.9167 8.41848 10.7851 8.10054 10.5506 7.86612C10.3162 7.6317 9.99827 7.5 9.66675 7.5ZM14.4167 7.5C14.0852 7.5 13.7673 7.6317 13.5329 7.86612C13.2984 8.10054 13.1667 8.41848 13.1667 8.75C13.1667 9.08152 13.2984 9.39946 13.5329 9.63388C13.7673 9.8683 14.0852 10 14.4167 10C14.7483 10 15.0662 9.8683 15.3006 9.63388C15.5351 9.39946 15.6667 9.08152 15.6667 8.75C15.6667 8.41848 15.5351 8.10054 15.3006 7.86612C15.0662 7.6317 14.7483 7.5 14.4167 7.5ZM15.4167 0C16.2787 0 17.1054 0.34241 17.7148 0.951903C18.3243 1.5614 18.6667 2.38805 18.6667 3.25V4H0.666748V3.25C0.666748 2.38805 1.00916 1.5614 1.61865 0.951903C2.22814 0.34241 3.05479 0 3.91675 0H15.4167Z"
                            fill="#10182C" />
                    </svg>
                    <el-date-picker v-model="airport.time" type="daterange" start-placeholder="Take-off"
                        end-placeholder="Return Date" :default-time="defaultTime" />
                </div>
            </div>
        </div>
        <div class="flex-full xl:flex-25% mt-2 xl:mt-0 xl:pl-[6px]">
            <button @click="search"
                class="bg-of-blue rounded-[14px] py-[18px] md:py-[24px] px-[12px] w-full text-white text-[20px] leading-[36px] font-semibold md:h-full flex items-center justify-center">Search
            Flights</button>
    </div>
</div></template>