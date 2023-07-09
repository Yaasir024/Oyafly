<template>
    <header class="sticky top-0 bg-of-main pb-1">
        <section class="flex items-center justify-end py-[6px] pr-[24px]">
            <div class="text-[13px]">Call support: +234-803-000-0031</div>
            <div class="text-[13px] font-semibold ml-4">Manage bookings</div>
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
                        <button class="px-[12px] py-[10px] rounded-[40px] text-white text-[16px] leading-[19px] font-bold bg-of-blue">Create an account</button>
                    </RouterLink>
                </div>
            </div>
        </nav>
    </header>
</template>