<template>
    <div class="hidden xl:flex flex-col relative w-full min-h-screen bg-[url('@/assets/slider-bg.jpeg')] bg-cover bg-center bg-no-repeat">
        <div class="absolute inset-0 bg-gradient-to-b from-transparent to-black opacity-100"></div>
    
        <div class="relative z-10 flex flex-col justify-between w-full h-full">
            <button class="flex justify-center items-center border rounded-full border-white p-4 w-12 h-12 ml-16 mt-20">
                <svg width="8" height="14" viewBox="0 0 8 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M6.4375 13.5312L0.71875 7.5625C0.5625 7.375 0.5 7.1875 0.5 7C0.5 6.84375 0.5625 6.65625 0.6875 6.5L6.40625 0.53125C6.6875 0.21875 7.1875 0.21875 7.46875 0.5C7.78125 0.78125 7.78125 1.25 7.5 1.5625L2.28125 7L7.53125 12.5C7.8125 12.7812 7.8125 13.2812 7.5 13.5625C7.21875 13.8438 6.71875 13.8438 6.4375 13.5312Z"  fill="white"/>
                </svg>
            </button>
            <div class="relative flex flex-col justify-between mb-12 mx-16 h-[316px]">
                <div class="flex flex-col space-y-3 w-full">
                    <span class="flex items-center justify-center text-white rounded-full bg-[#0761E2] px-3 py-2 w-[78px] h-[32px]">{{ items[selectedIndex].title }}</span>
                    <h3 class="text-white text-2xl leading-[33.6px] font-semibold">{{ items[selectedIndex].subtitle }}</h3>
                    <h4 class="text-[#909090] font-medium text-xl leading-[28px]">{{ items[selectedIndex].description }}</h4>
                </div>
                <div class="flex justify-between w-full">
                    <div class="flex items-center space-x-4">
                        <span v-for="(selector, index) in selectors" :key="index" :class="{ 'bg-white': selectedIndex === index, 'bg-[#222222]': selectedIndex !== index }" class="w-[96px] h-[4px] cursor-pointer" @click="select(index)"></span>
                    </div>
                    <div class="flex items-center">
                        <button @click="previous" class="flex justify-center items-center rounded-full w-16 h-16 group">
                            <svg width="18" height="29" viewBox="0 0 18 29" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M15 29C14.4375 29 13.9375 28.8125 13.5625 28.4375L1.5625 16.4375C0.75 15.6875 0.75 14.375 1.5625 13.625L13.5625 1.625C14.3125 0.8125 15.625 0.8125 16.375 1.625C17.1875 2.375 17.1875 3.6875 16.375 4.4375L5.8125 15L16.375 25.625C17.1875 26.375 17.1875 27.6875 16.375 28.4375C16 28.8125 15.5 29 15 29Z" class="group-hover:fill-white" fill="#3A3A3A"/>
                            </svg>
                        </button>
                        <button @click="next" class="flex justify-center items-center rounded-full w-16 h-16 group">
                            <svg width="18" height="29" viewBox="0 0 18 29" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M3 29C2.4375 29 1.9375 28.8125 1.5625 28.4375C0.75 27.6875 0.75 26.375 1.5625 25.625L12.125 15L1.5625 4.4375C0.75 3.6875 0.75 2.375 1.5625 1.625C2.3125 0.8125 3.625 0.8125 4.375 1.625L16.375 13.625C17.1875 14.375 17.1875 15.6875 16.375 16.4375L4.375 28.4375C4 28.8125 3.5 29 3 29Z" class="group-hover:fill-white" fill="#3A3A3A"/>
                            </svg>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const selectors = ref([0, 1, 2]);
const selectedIndex = ref(0);

const items = ref([
  { title: 'Cursos', subtitle: 'Plataforma de cursos completa', description: 'Lorem ipsum nisl etiam himenaeos ligula augue vehicula gravida tincidunt, etiam magna sapien gravida sodales sed vel pulvinar suspendisse, morbi mi proin urna ornare posuere donec aptent. orci vivamus primis fusce lacinia libero nostra aliquam vestibulum' },
  { title: 'Cursos', subtitle: 'Plataforma de cursos 2', description: 'Mussum Ipsum, cacilds vidis litro abertis. Vehicula non. Ut sed ex eros. Vivamus sit amet nibh non tellus tristique interdum. Diuretics paradis num copo é motivis de denguis. Casamentiss faiz malandris se pirulitá. Quem manda na minha terra sou euzis!' },
  { title: 'Cursos', subtitle: 'Plataforma de cursos 3', description: 'Mussum Ipsum, cacilds vidis litro abertis. Mauris nec dolor in eros commodo tempor. Aenean aliquam molestie leo, vitae iaculis nisl. Pellentesque nec nulla ligula. Donec gravida turpis a vulputate ultricies. Interagi no mé, cursus quis, vehicula ac nisi. Quem num gosta di mé, boa gentis num é.' }
]);

function select(index) {
  selectedIndex.value = index;
}

function previous() {
  selectedIndex.value = (selectedIndex.value - 1 + selectors.value.length) % selectors.value.length;
}

function next() {
  selectedIndex.value = (selectedIndex.value + 1) % selectors.value.length;
}
</script>