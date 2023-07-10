<script setup>
import { ref } from 'vue';

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
    <main class="bg-of-main  min-h-screen">
        <div class="px-4 sm:px-6">
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
                <nav class="px-[24px] py-[12px]  flex items-center justify-between bg-white rounded-[20px]">
                    <img src="/logo.svg" alt="" class="">
                </nav>
            </header>
            <div class=""></div>
            <section class="flex mt-[40px]">
                <div class="pr-2 w-full">
                    <div class="">
                        <h3 class="text-[20px] leading-[19px] font-semibold font-pp">Your details</h3>
                        <div class="mt-[12px] w-full rounded-[20px] bg-white border border-[#D7E6FE] p-4">
                            <div class="px-[20px] py-[16px] bg-[#FFE224] rounded-xl relative">
                                <h3 class="text-[16px] leading-[19px] font-semibold">Double-check your personal details</h3>
                                <h3 class="text-[14px] leading-[16px] mt-[10px]">Please enter the names as they appear in
                                    your travel documentation</h3>
                            </div>

                            <div class="mt-[35px]">
                                <div class="">
                                    <div class="pb-[19px] border-b border-of-gray">
                                        <span class="text-[14px] leading-[16px] font-medium">Traveler 1</span>
                                    </div>
                                    <div class="mt-[24px] flex items-center gap-x-[12px]">
                                        <div class="flex flex-col">
                                            <span class="text-[14px] leading-[19px] font-medium mb-[12px]">Title</span>
                                            <div
                                                class="px-[12px] py-[18px] border border-of-gray outline-none rounded-xl flex items-center">
                                                <span class="mr-1">Select</span>
                                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16"
                                                    viewBox="0 0 16 16" fill="none">
                                                    <path
                                                        d="M4.06798 5.33337C3.35198 5.33337 2.96931 6.17671 3.44131 6.71537L7.12198 10.922C7.23148 11.0472 7.36647 11.1475 7.5179 11.2162C7.66932 11.2849 7.83369 11.3204 7.99998 11.3204C8.16626 11.3204 8.33063 11.2849 8.48206 11.2162C8.63349 11.1475 8.76848 11.0472 8.87798 10.922L12.5593 6.71537C13.0306 6.17671 12.648 5.33337 11.9326 5.33337H4.06731H4.06798Z"
                                                        fill="#10182C" />
                                                </svg>
                                            </div>
                                        </div>
                                        <div class="flex flex-col w-full">
                                            <span class="text-[14px] leading-[19px] font-medium mb-[12px]">First name</span>
                                            <input type="text" placeholder="As written on passport"
                                                class="px-[12px] py-[18px] border border-of-gray outline-none rounded-xl w-full">
                                        </div>
                                        <div class="flex flex-col w-full">
                                            <span class="text-[14px] leading-[19px] font-medium mb-[12px]">Last name</span>
                                            <input type="text" placeholder="As written on passport"
                                                class="px-[12px] py-[18px] border border-of-gray outline-none rounded-xl w-full">
                                        </div>
                                        <button class="">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"
                                                viewBox="0 0 20 20" fill="none">
                                                <path
                                                    d="M8.33342 4.16667H11.6667C11.6667 3.72464 11.4912 3.30072 11.1786 2.98816C10.866 2.67559 10.4421 2.5 10.0001 2.5C9.55805 2.5 9.13413 2.67559 8.82157 2.98816C8.50901 3.30072 8.33342 3.72464 8.33342 4.16667ZM7.08342 4.16667C7.08342 3.78364 7.15886 3.40437 7.30543 3.05051C7.45201 2.69664 7.66685 2.37511 7.93769 2.10427C8.20852 1.83343 8.53006 1.61859 8.88392 1.47202C9.23779 1.32544 9.61706 1.25 10.0001 1.25C10.3831 1.25 10.7624 1.32544 11.1162 1.47202C11.4701 1.61859 11.7916 1.83343 12.0625 2.10427C12.3333 2.37511 12.5482 2.69664 12.6947 3.05051C12.8413 3.40437 12.9167 3.78364 12.9167 4.16667H17.7084C17.8742 4.16667 18.0331 4.23251 18.1504 4.34973C18.2676 4.46694 18.3334 4.62591 18.3334 4.79167C18.3334 4.95743 18.2676 5.1164 18.1504 5.23361C18.0331 5.35082 17.8742 5.41667 17.7084 5.41667H16.6084L15.6334 15.5092C15.5586 16.2825 15.1985 17.0002 14.6231 17.5224C14.0478 18.0445 13.2987 18.3336 12.5217 18.3333H7.47842C6.70163 18.3334 5.95267 18.0442 5.37754 17.5221C4.80241 16.9999 4.44236 16.2823 4.36758 15.5092L3.39175 5.41667H2.29175C2.12599 5.41667 1.96702 5.35082 1.84981 5.23361C1.7326 5.1164 1.66675 4.95743 1.66675 4.79167C1.66675 4.62591 1.7326 4.46694 1.84981 4.34973C1.96702 4.23251 2.12599 4.16667 2.29175 4.16667H7.08342ZM8.75008 8.125C8.75008 7.95924 8.68423 7.80027 8.56702 7.68306C8.44981 7.56585 8.29084 7.5 8.12508 7.5C7.95932 7.5 7.80035 7.56585 7.68314 7.68306C7.56593 7.80027 7.50008 7.95924 7.50008 8.125V14.375C7.50008 14.5408 7.56593 14.6997 7.68314 14.8169C7.80035 14.9342 7.95932 15 8.12508 15C8.29084 15 8.44981 14.9342 8.56702 14.8169C8.68423 14.6997 8.75008 14.5408 8.75008 14.375V8.125ZM11.8751 7.5C11.7093 7.5 11.5504 7.56585 11.4331 7.68306C11.3159 7.80027 11.2501 7.95924 11.2501 8.125V14.375C11.2501 14.5408 11.3159 14.6997 11.4331 14.8169C11.5504 14.9342 11.7093 15 11.8751 15C12.0408 15 12.1998 14.9342 12.317 14.8169C12.4342 14.6997 12.5001 14.5408 12.5001 14.375V8.125C12.5001 7.95924 12.4342 7.80027 12.317 7.68306C12.1998 7.56585 12.0408 7.5 11.8751 7.5Z"
                                                    fill="#10182C" />
                                            </svg>
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="w-[480px]">
                    <h3 class="text-[20px] leading-[19px] font-semibold font-pp">Your booking</h3>
                    <div class="mt-[12px] w-full rounded-[20px] bg-white border border-[#D7E6FE] p-4">
                        <div class="text-[18px] leading-[19px] font-pp pb-2 border-b border-of-gray">
                            Pay for trip
                        </div>
                        <div class="mt-[24px]">
                            <div class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16"
                                    fill="none">
                                    <path
                                        d="M7.01533 2.94002L8.262 3.95002C8.13533 4.08669 8.024 4.21535 7.93 4.32802C7.84733 4.42802 7.77133 4.46002 7.734 4.46802L5.42533 4.94935L5.17067 4.49469C4.712 3.67602 5.304 2.66669 6.242 2.66669C6.52333 2.66669 6.79667 2.76335 7.01533 2.94002ZM11.1287 3.00202C12.62 2.88669 13.7347 3.83069 14.3647 4.55269C14.6907 4.92602 14.756 5.39802 14.6167 5.80802C14.5444 6.01317 14.4263 6.1991 14.2712 6.35162C14.1162 6.50413 13.9283 6.6192 13.722 6.68802L10.1413 7.92269L7.984 10.7994C7.78889 11.0595 7.50559 11.2395 7.18723 11.3057C6.86886 11.3719 6.53727 11.3198 6.25463 11.159C5.97198 10.9982 5.75768 10.7398 5.6519 10.4323C5.54611 10.1249 5.5561 9.78934 5.68 9.48869L6.01867 8.66669L3.818 9.09002C3.59674 9.13255 3.36881 9.12566 3.15052 9.06985C2.93223 9.01404 2.72896 8.91069 2.55526 8.76718C2.38156 8.62367 2.24172 8.44356 2.14573 8.23971C2.04974 8.03587 1.99998 7.81333 2 7.58802V5.12802C1.99983 4.87739 2.08319 4.63385 2.23689 4.43589C2.39059 4.23793 2.60588 4.09683 2.84874 4.03489C3.09159 3.97296 3.34816 3.99371 3.5779 4.09388C3.80764 4.19405 3.99745 4.36792 4.11733 4.58802L4.76133 5.76802L7.87 5.12135C8.07933 5.07735 8.28133 4.94802 8.44333 4.75402C8.69 4.45602 9.06267 4.05069 9.50867 3.70669C9.94867 3.36802 10.5087 3.04935 11.1287 3.00202ZM2.5 13C2.36739 13 2.24022 13.0527 2.14645 13.1465C2.05268 13.2402 2 13.3674 2 13.5C2 13.6326 2.05268 13.7598 2.14645 13.8536C2.24022 13.9473 2.36739 14 2.5 14H13.5C13.6326 14 13.7598 13.9473 13.8536 13.8536C13.9473 13.7598 14 13.6326 14 13.5C14 13.3674 13.9473 13.2402 13.8536 13.1465C13.7598 13.0527 13.6326 13 13.5 13H2.5Z"
                                        fill="#10182C" />
                                </svg>
                                <span class="ml-[6px] text-[16px] leading-[17px] font-semibold font-pp">Leaving</span>
                                <span class="ml-[6px] text-[16px] leading-[17px] font-pp">12/05/2023</span>
                            </div>
                            <div class="flex items-center mt-[24px]">
                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16"
                                    fill="none">
                                    <path
                                        d="M6.66678 3.35932V3.87798L8.68478 4.67932H10.0974L9.26411 2.80732C8.66811 1.46798 6.66678 1.89398 6.66678 3.35932ZM8.48011 5.31598L5.66678 4.19798V3.17132C5.66678 2.01265 4.16078 1.56198 3.52478 2.53065L2.25144 4.46932C2.12766 4.65801 2.04697 4.87166 2.01513 5.09507C1.98328 5.31849 2.00105 5.54617 2.06718 5.76194C2.13331 5.9777 2.24618 6.17625 2.39774 6.34345C2.54931 6.51064 2.73585 6.64239 2.94411 6.72932L5.27944 7.70532L3.91611 8.97065C2.83144 9.97798 3.91344 11.7473 5.30411 11.2407L9.81144 9.59798L12.1201 10.562C12.3263 10.648 12.5506 10.6818 12.773 10.6604C12.9955 10.6389 13.2091 10.5629 13.3951 10.4391C13.5811 10.3152 13.7337 10.1473 13.8392 9.95037C13.9447 9.75341 14 9.53344 14.0001 9.30998V8.48998C14.0002 8.07714 13.919 7.66832 13.761 7.28688C13.6031 6.90543 13.3716 6.55884 13.0797 6.26688C12.7878 5.97492 12.4412 5.74333 12.0598 5.58532C11.6784 5.42731 11.2696 5.34598 10.8568 5.34598H8.63944C8.58513 5.34611 8.53063 5.33593 8.48011 5.31598ZM2.00011 13.5C2.00011 13.3674 2.05279 13.2402 2.14656 13.1464C2.24033 13.0527 2.3675 13 2.50011 13H13.5001C13.6327 13 13.7599 13.0527 13.8537 13.1464C13.9474 13.2402 14.0001 13.3674 14.0001 13.5C14.0001 13.6326 13.9474 13.7598 13.8537 13.8535C13.7599 13.9473 13.6327 14 13.5001 14H2.50011C2.3675 14 2.24033 13.9473 2.14656 13.8535C2.05279 13.7598 2.00011 13.6326 2.00011 13.5Z"
                                        fill="#10182C" />
                                </svg>
                                <span class="ml-[6px] text-[16px] leading-[17px] font-semibold font-pp">Returning</span>
                                <span class="ml-[6px] text-[16px] leading-[17px] font-pp">09/02/2024</span>
                            </div>
                            <div class="mt-[100px]">
                                <div class="flex items-center justify-between pt-[12px] border-t-2 border-of-gray">
                                    <span class="text-[16px] leading-[17px] font-pp">Travellers</span>
                                    <span class="text-[16px] leading-[17px] font-semibold font-pp">2 Adults</span>
                                </div>
                                <div
                                    class="flex items-center justify-between pt-[12px] border-t-2 border-of-gray mt-[24px]">
                                    <span class="text-[16px] leading-[17px] font-pp">Baggage Per passenger</span>
                                    <span class="text-[16px] leading-[17px] font-semibold font-pp">1x 20kg checkin
                                        allowance</span>
                                </div>
                                <div
                                    class="flex items-center justify-between pt-[12px] border-t-2 border-of-gray mt-[24px]">
                                    <span class="text-[16px] leading-[17px] font-pp">Payment with : VISA
                                        Electron/Debit</span>
                                    <span class="text-[16px] leading-[17px] font-semibold font-pp">£ 4.99</span>
                                </div>
                                <div
                                    class="flex items-center justify-between pt-[12px] pb-[24px] border-y-2 border-of-gray mt-[24px]">
                                    <span class="text-[16px] leading-[17px] font-pp">Booking fee</span>
                                    <span class="text-[16px] leading-[17px] font-semibold font-pp">£ 4.99</span>
                                </div>
                                <div class="flex items-end mt-[12px]">
                                    <span class="text-[24px] leading-[25px] font-semibold font-pp mr-2">₦200,000</span>
                                    <span
                                        class="text-[18px] leading-[18px] line-through font-pp font-semibold text-of-dark/80">₦536,000</span>
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
                                <button class="rounded-xl p-3 bg-of-blue flex items-center justify-center w-full">
                                    <span class="text-[14px] leading-normal font-semibold text-white">Continue to
                                        checkout</span>
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
            </section>
        </div>
    </main>
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
}</style>