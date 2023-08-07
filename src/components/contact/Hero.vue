<script setup>
import { ref } from 'vue';

const selected = ref('2')
let accordionData = [
    {
        id: '1',
        question: "How do I book a flight on Oyafly?",
        answer: "We accept a variety of payment methods, including credit cards, debit cards, and mobile payment options. You can choose the method that is most convenient for you during the checkout process.",
    },
    {
        id: '2',
        question: "What payment methods are accepted on Oyafly?",
        answer: "We accept a variety of payment methods, including credit cards, debit cards, and mobile payment options. You can choose the method that is most convenient for you during the checkout process.",
    },
    {
        id: '3',
        question: "Can I manage my booking after it's confirmed?",
        answer: "We accept a variety of payment methods, including credit cards, debit cards, and mobile payment options. You can choose the method that is most convenient for you during the checkout process.",
    },
    {
        id: '4',
        question: "What happens if my flight is delayed or canceled?",
        answer: "We accept a variety of payment methods, including credit cards, debit cards, and mobile payment options. You can choose the method that is most convenient for you during the checkout process.",
    },
    {
        id: '5',
        question: "Are there any additional fees during the booking process?",
        answer: "We accept a variety of payment methods, including credit cards, debit cards, and mobile payment options. You can choose the method that is most convenient for you during the checkout process.",
    },
    {
        id: '6',
        question: "Is my personal and payment information secure on Oyafly?",
        answer: "We accept a variety of payment methods, including credit cards, debit cards, and mobile payment options. You can choose the method that is most convenient for you during the checkout process.",
    },
    {
        id: '7',
        question: "How can I contact Oyafly customer support?",
        answer: "We accept a variety of payment methods, including credit cards, debit cards, and mobile payment options. You can choose the method that is most convenient for you during the checkout process.",
    },
]

const toggleAccordion = (id) => {
    if (selected.value != id) {
        selected.value = id
    } else if (selected.value == id) {
        selected.value = ''
    }
}
</script>

<template>
    <section class="mt-[10px] ">
        <div class="relative p-[24px] pb-[36px] bg-white rounded-[20px] overflow-hidden flex items-end justify-between flex-wrap">
            <div class="flex-full lg:flex-50% pt-[16px] flex flex-col pb-[76px]">
                <div class="">
                    <h1
                        class="text-[52px] sm:text-[64px] md:text-[72px] leading-[48px] sm:leading-[61px] font-semibold font-pp max-w-[580px] tracking-[-2.56px]">
                        Got questions?
                    </h1>
                    <p
                        class="mt-[12px] text-[18px] sm:text-[24px] leading-[22px] sm:leading-[36px] max-w-[545px] tracking-[0.24px] text-of-dark/60">
                        Get in touch with the Oyafly team and we’ll get back to you and help as soon as we can!
                    </p>

                </div>
                <div class="mt-[120px] lg:max-w-[545px]">
                    <form action="" class="w-full">
                        <div class="w-full pb-[12px] border-b">
                            <h1 class="text-[24px] leading-[24px] tracking-[-0.48px] font-semibold">Contact us</h1>
                        </div>
                        <div class="flex flex-col mt-[24px]">
                            <label class="text-[14px] leading-[16px] font-medium tracking-[0.14px] mb-3">
                                Your name
                            </label>
                            <input type="text" placeholder="Enter your name"
                                class="border border-[#D7E6FE] rounded-xl px-3 py-[18px] h-[48px] text-[16px] tracking-[0.16px] outline-none">
                        </div>
                        <div class="flex flex-col mt-[24px]">
                            <label class="text-[14px] leading-[16px] font-medium tracking-[0.14px] mb-3">
                                Your email
                            </label>
                            <input type="text" placeholder="Enter your name"
                                class="border border-[#D7E6FE] rounded-xl px-3 py-[18px] h-[48px] text-[16px] tracking-[0.16px] outline-none">
                        </div>
                        <div class="flex flex-col mt-[24px]">
                            <label class="text-[14px] leading-[16px] font-medium tracking-[0.14px] mb-3">
                                What would you like to learn?
                            </label>
                            <textarea placeholder="I’d like to learn about corporate bookings"
                                class="border border-[#D7E6FE] rounded-xl px-3 py-[12px] text-[16px] tracking-[0.16px] outline-none">

                            </textarea>
                        </div>
                        <button
                            class="mt-[48px] w-full rounded-full py-[14px] px-[20px] bg-of-blue text-center text-[16px] font-bold text-white">
                            Send Message
                        </button>
                    </form>
                </div>
            </div>
            <div class="flex-full lg:flex-50% lg:pl-8 ">
                <div class="w-full pb-[12px] border-b">
                    <h1 class="text-[24px] leading-[24px] tracking-[-0.48px] font-semibold">General Questions</h1>
                </div>
                <div v-for="data in accordionData" :key="data.id" class="border-b border-[#D7E6FE] lg:px-3">
                    <div @click="toggleAccordion(data.id)" class="question flex items-center py-4 cursor-pointer">
                        <button class="">
                            <svg class="transition-all duration-300 ease-in-out" :class="data.id == selected ? 'rotate-0' : 'rotate-180'" width="16" height="10" viewBox="0 0 16 10" fill="none"
                                xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M1.17093 8.805C1.07212 8.69211 1.01205 8.54244 1.00163 8.38321C0.991205 8.22397 1.03113 8.06576 1.11414 7.93732L1.17093 7.86264L7.58854 0.528223C7.68733 0.415301 7.81829 0.346643 7.95762 0.334734C8.09694 0.322824 8.23538 0.368453 8.34777 0.463325L8.41311 0.528223L14.8307 7.86264C14.9342 7.98177 14.9945 8.14109 14.9996 8.3088C15.0048 8.47652 14.9544 8.64029 14.8586 8.76744C14.7628 8.89459 14.6285 8.97576 14.4826 8.99475C14.3367 9.01374 14.1899 8.96916 14.0715 8.8699L14.0062 8.805L8.00083 1.94177L1.99549 8.805C1.8861 8.92987 1.73782 9 1.58321 9C1.4286 9 1.28032 8.92987 1.17093 8.805Z"
                                    fill="#10182C" stroke="#10182C" stroke-width="0.4" />
                            </svg>
                        </button>
                        <h3 class="ml-[17px] text-[16px] leading-[16px] font-pp font-semibold tracking-[-0.16px]">
                            {{ data.question }}
                        </h3>
                    </div>
                    <div class="answer pl-[36px] overflow-hidden transition-all duration-300 ease-in-out" :class="data.id == selected ? 'max-h-[999px]' : 'max-h-0'">
                        <div class="w-full pb-[18px]">
                            <p class="text-[16px] leading-[26px] text-[#10182C]/60">
                                {{ data.answer }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
</section></template>