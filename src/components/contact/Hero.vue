<template>
    <section class="mt-[10px] ">
        <div class="relative p-[24px] bg-white rounded-[20px] overflow-hidden flex justify-between">
            <div class="pt-[16px] flex flex-col">
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
                <div class="mt-[120px] max-w-[545px]">
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
                        <button class="mt-[48px] w-full rounded-full py-[14px] px-[20px] bg-of-blue text-center text-[16px] font-bold text-white">
                            Send Message
                        </button>
                    </form>
                </div>
            </div>
            <div class="pl-8 hidden ">

                <div class="max-w-[450px] 2xl:max-w-[590px] rounded-[15px] overflow-hidden">
                    <video class="" autoplay loop muted>
                        <source src="@/assets/images/about/hero/vid.mp4" type="video/mp4">
                    </video>
                </div>
            </div>
        </div>
</section></template>