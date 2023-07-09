<template>
    <header class="sticky top-0 bg-of-main pb-1">
        <section class="flex items-center justify-end py-[6px] pr-[24px]">
            <div class="text-[13px]">Call support: +234-803-000-0031</div>
            <div class="text-[13px] font-semibold ml-4">Manage bookings</div>
            <button class=" ml-4 flex items-center">
                <span class="text-[13px] font-semibold">
                    NGN
                </span>
                <svg class="ml-[4px]" width="10" height="7" viewBox="0 0 10 7" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                        d="M1.06798 0.333374C0.351977 0.333374 -0.0306894 1.17671 0.441311 1.71537L4.12198 5.92204C4.23148 6.04718 4.36647 6.14747 4.5179 6.21619C4.66932 6.2849 4.83369 6.32044 4.99998 6.32044C5.16626 6.32044 5.33063 6.2849 5.48206 6.21619C5.63349 6.14747 5.76848 6.04718 5.87798 5.92204L9.55931 1.71537C10.0306 1.17671 9.64798 0.333374 8.93264 0.333374H1.06731H1.06798Z"
                        fill="#10182C" />
                </svg>
            </button>
        </section>
        <nav class="px-[24px] py-[12px]  flex items-center justify-between bg-white rounded-[20px]">
            <img src="/logo.svg" alt="" class="">
            <div class="flex items-center border-l border-[#DCDADA] pl-[20px]">
                <ul class="flex items-center mr-[20px]">
                    <li class="text-[16px] leading-[19px] mr-[20px]">
                        <RouterLink to="/">About Us</RouterLink>
                    </li>
                    <li class="text-[16px] leading-[19px] mr-[20px]">
                        <RouterLink to="/">Blog</RouterLink>
                    </li>
                    <li class="text-[16px] leading-[19px]">
                        <RouterLink to="/">Careers</RouterLink>
                    </li>
                </ul>
                <div class="text-[16px] leading-[19px] font-semibold mr-[20px]">
                    <RouterLink to="/" class="font-semibold">Sign in</RouterLink>
                </div>
                <div class="">
                    <RouterLink to="/">
                        <button
                            class="px-[12px] py-[10px] rounded-[40px] text-white text-[16px] leading-[19px] font-bold bg-of-blue">Create
                            an account</button>
                    </RouterLink>
                </div>
            </div>
        </nav>
    </header>
</template>