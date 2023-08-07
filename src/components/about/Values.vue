<template>
    <div class="bg-white rounded-[20px] px-[24px] pt-[40px] mt-[8px] pb-[60px]">
        <div class="">
            <h1 class="text-[38px] sm:text-[48px] leading-[26px] font-pp font-semibold tracking-[-0.96px]">
                Our values
            </h1>
            <p
                class="mt-[12px] text-[18px] sm:text-[24px] leading-[28px] sm:leading-[36px] tracking-[0.24px] text-of-dark/60 max-w-[635px]">
                Nurturing a culture of excellence, transparency, and customer-centricity to redefine the travel experience.
            </p>
        </div>
        <div class="mt-[72px] flex flex-wrap pb-[32px] border-b-2 border-dashed border-[#D7E6FE] gap-y-[20px]">
            <div class="md:flex-50% xl:flex-25% pr-1">
                <div class="card-one bg-[#00EA8A] p-3 rounded-[14px]">
                    <div class="h-[240px] w-full"></div>
                    <div class="pt-[16px] px-[12px] pb-[24px] bg-white rounded-md">
                        <h4 class="text-[20px] font-semibold font-pp text-of-dark/80">Exceptional Service</h4>
                        <p class="mt-2 text-[16px] leading-[27.5px] tracking-[0.16px] text-of-dark/60">
                            Delivering exceptional service that goes above and beyond, ensuring memorable travel experiences
                            for every customer.
                        </p>
                    </div>
                </div>
            </div>
            <div class="md:flex-50% xl:flex-25% pr-1">
                <div class="card-two bg-[#00D1FF] p-3 rounded-[14px]">
                    <div class="h-[240px] w-full"></div>
                    <div class="pt-[16px] px-[12px] pb-[24px] bg-white rounded-md">
                        <h4 class="text-[20px] font-semibold font-pp text-of-dark/80">Customer-centric</h4>
                        <p class="mt-2 text-[16px] leading-[27.5px] tracking-[0.16px] text-of-dark/60">
                            Putting our customers at the heart of everything we do, crafting personalized solutions and
                            anticipating their needs.
                        </p>
                    </div>
                </div>
            </div>

            <div class="md:flex-50% xl:flex-25% pr-1">
                <div class="card-three bg-[#F3E909] p-3 rounded-[14px]">
                    <div class="h-[240px] w-full"></div>
                    <div class="pt-[16px] px-[12px] pb-[24px] bg-white rounded-md">
                        <h4 class="text-[20px] font-semibold font-pp text-of-dark/80">Transparency</h4>
                        <p class="mt-2 text-[16px] leading-[27.5px] tracking-[0.16px] text-of-dark/60">
                            Embracing clarity and honesty in our operations, policies, communication; fostering trust and
                            reliability with our all valued flyers.
                        </p>
                    </div>
                </div>
            </div>
            <div class="md:flex-50% xl:flex-25% pr-1">
                <div class="card-four bg-[#D492FF] p-3 rounded-[14px]">
                    <div class="h-[240px] w-full"></div>
                    <div class="pt-[16px] px-[12px] pb-[24px] bg-white rounded-md">
                        <h4 class="text-[20px] font-semibold font-pp text-of-dark/80">Accessible</h4>
                        <p class="mt-2 text-[16px] leading-[27.5px] tracking-[0.16px] text-of-dark/60">
                            Making travel accessible to every Nigerian, creating inclusive experiences that cater to diverse
                            needs and preferences.
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card-one {
    position: relative;
    background-image: url(./../../assets/images/about/values/1.png);
    background-size: cover;
    background-position: top;
}
.card-two {
    position: relative;
    background-image: url(./../../assets/images/about/values/2.png);
    background-size: cover;
    background-position: top;
}
.card-three {
    position: relative;
    background-image: url(./../../assets/images/about/values/3.png);
    background-size: cover;
    background-position: top;
}
.card-four {
    position: relative;
    background-image: url(./../../assets/images/about/values/4.png);
    background-size: cover;
    background-position: top;
}
.img {
    transition: all .3s ease-in-out;
}

.image-container:hover .img {
    transform: scale(1.02);
}
</style>