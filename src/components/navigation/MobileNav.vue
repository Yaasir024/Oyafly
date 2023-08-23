<script setup>
const emit = defineEmits(["close"]) 

const closeOnRoute = () => {
    emit('close')
}
</script>

<template>
    <div class="h-screen w-screen xs:w-[70vw] fixed top-0 bottom-0 right-0 bg-[#333] ml-auto text-white flex flex-col justify-between z-50">
        <div class="">
            <div class="flex items-center justify-end px-3 py-4 border-b">
                <button class="text-white" @click="$emit('close')">
                    <svg width="24" height="24" fill="currentColor" clip-rule="evenodd" fill-rule="evenodd"
                        stroke-linejoin="round" stroke-miterlimit="2" viewBox="0 0 24 24"
                        xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="m12 10.93 5.719-5.72c.146-.146.339-.219.531-.219.404 0 .75.324.75.749 0 .193-.073.385-.219.532l-5.72 5.719 5.719 5.719c.147.147.22.339.22.531 0 .427-.349.75-.75.75-.192 0-.385-.073-.531-.219l-5.719-5.719-5.719 5.719c-.146.146-.339.219-.531.219-.401 0-.75-.323-.75-.75 0-.192.073-.384.22-.531l5.719-5.719-5.72-5.719c-.146-.147-.219-.339-.219-.532 0-.425.346-.749.75-.749.192 0 .385.073.531.219z" />
                    </svg>
                </button>
            </div>
            <ul class="flex flex-col ">
                <li class="flex items-center justify-center text-[20px] leading-[19px] py-4 border-b">
                    <RouterLink to="/about" class="w-full text-center" @click="closeOnRoute">About Us</RouterLink>
                </li>
                <li class="flex items-center justify-center text-[20px] leading-[19px] py-4 border-b">
                    <RouterLink to="/contact-us" class="w-full text-center" @click="closeOnRoute">Contact</RouterLink>
                </li>
            </ul>
        </div>
        <div class="pb-4">
            <li class="flex items-center justify-center text-[20px] leading-[19px] py-4 border-y">
                <RouterLink to="/" class="w-full text-center" @click="closeOnRoute">Sign in</RouterLink>
            </li>

        </div>
    </div>
    
</template>