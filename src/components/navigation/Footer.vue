<template>
    <footer class="mt-2 bg-[#D7E6FE] rounded-[20px]">
        <div class="px-4 sm:px-6">
            <div class="pt-[32px] px-[24px] flex justify-between flex-col lg:flex-row">
                <div class="">
                    <img src="/logo-icon.svg" alt="" class="">
                    <div class="mt-[85px]">
                        <p class="text-[16px] leading-[32px] font-semibold">
                            Oya Fly Ltd.
                        </p>
                        <p class="text-[16px] leading-[32px]">
                            111 Allen Avenue Ikeja, Lagos <br>
                            hello@oyafly.co <br>
                            08030000031
                        </p>
                    </div>
                </div>
                <div class="pt-[24px] pr-0 2xl:pr-[180px]">
                    <h3 class="text-[16px] leading-[19px] font-bold">
                        Subscribe for our special deals
                    </h3>
                    <h4 class="text-[16px] leading-[28px] mt-[4px]">
                        Save with our latest fares and offers.
                    </h4>
                    <div class="mt-2">
                        <form @submit.prevent class="flex items-center sm:min-w-[400px] w-full bg-white rounded-xl p-[4px]">
                            <input type="text" placeholder="Your email address"
                                class="w-full text-[14px] leading-[25px] placeholder:text-of-dark placeholder:font-normal outline-none px-2 py-[5px]">
                            <button
                                class="ml-2 px-[8px] py-[5px] bg-of-dark rounded-lg text-[14px] text-white leading-[25px] font-semibold">Subscribe</button>
                        </form>
                    </div>
                    <div class="mt-[40px] flex flex-col xs:flex-row">
                        <ul class="mr-[56px]">
                            <li class="">
                                <h3 class="text-[16px] leading-[32px] font-bold">
                                    Plan your trip
                                </h3>
                            </li>
                            <li class="text-[16px] leading-[32px]">
                                <RouterLink to="/">
                                    Manage bookings
                                </RouterLink>
                            </li>
                            <li class="text-[16px] leading-[32px]">
                                <RouterLink to="/">
                                    Explore destinations
                                </RouterLink>
                            </li>
                            <li class="text-[16px] leading-[32px]">
                                <RouterLink to="/">
                                    Contact helpdesk
                                </RouterLink>
                            </li>
                        </ul>
                        <ul class="">
                            <li class="">
                                <h3 class="text-[16px] leading-[32px] font-bold">
                                    Go with Oyafly
                                </h3>
                            </li>
                            <li class="text-[16px] leading-[32px]">
                                <RouterLink to="/">
                                    About us
                                </RouterLink>
                            </li>
                            <li class="text-[16px] leading-[32px]">
                                <RouterLink to="/">
                                    Careers
                                </RouterLink>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>

        </div>
        <img src="@/assets/images/nav/footer-pattern.svg" alt="" class="mt-[50px]">
    </footer>
</template>