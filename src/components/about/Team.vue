<template>
    <div class="bg-white rounded-[20px] px-[24px] pt-[40px] mt-[8px] pb-[60px]">
        <div class="">
            <h1 class="text-[38px] sm:text-[48px] leading-[26px] font-pp font-semibold tracking-[-0.96px]">
                Meet the team
            </h1>
            <p class="mt-[12px] text-[18px] sm:text-[24px] leading-[28px] sm:leading-[36px] tracking-[0.24px] text-of-dark/60 max-w-[635px]">
                Get to know the incredible people of Oyafly – the team that takes you all the way there and back
            </p>
        </div>
        <div class="mt-[72px] flex flex-wrap pb-[28px] border-b-2 border-[#D7E6FE]">
            <div class="flex-50% md:flex-33.33% p-[2px]">
                <div class="image-container rounded-tl-[14px] overflow-hidden">
                    <img src="@/assets/images/about/team/1.png" alt="" class="img">
                </div>
            </div>
            <div class="flex-50% md:flex-33.33% p-[2px]">
                <div class="image-container rounded-tr-[14px] md:rounded-tr-0 overflow-hidden">
                    <img src="@/assets/images/about/team/2.png" alt="" class="img">
                </div>
            </div>
            <div class="flex-50% md:flex-33.33% p-[2px]">
                <div class="image-container rounded-tr-[14px] overflow-hidden">
                    <img src="@/assets/images/about/team/3.png" alt="" class="img">
                </div>
            </div>
            <div class="flex-50% md:flex-33.33% p-[2px]">
                <div class="image-container rounded-bl-[14px] overflow-hidden">
                    <img src="@/assets/images/about/team/4.png" alt="" class="img">
                </div>
            </div>
            <div class="flex-50% md:flex-33.33% p-[2px]">
                <div class="image-container overflow-hidden">
                    <img src="@/assets/images/about/team/5.png" alt="" class="img">
                </div>
            </div>
            <div class="flex-50% md:flex-33.33% p-[2px]">
                <div class="image-container rounded-br-[14px] overflow-hidden">
                    <img src="@/assets/images/about/team/6.png" alt="" class="img">
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.img {
    transition: all .3s ease-in-out;
}
.image-container:hover .img {
    transform: scale(1.02);
}
</style>