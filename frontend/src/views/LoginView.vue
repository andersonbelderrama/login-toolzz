<template>
  <div class="flex justify-center xl:justify-between dark:bg-[#232323]">
    <Slider/>
    <div class="md:w-[644px] w-full xl:p-6 flex flex-col bg-white dark:bg-[#232323]">
      <div class="flex justify-between items-center border-b border-black/10 dark:border-white/10 p-6 md:hidden">
        <button class="flex justify-center items-center border rounded-full border-black dark:border-white p-4 w-12 h-12">
          <IconBackButton />
        </button>
        <button class="text-black dark:text-white py-5 px-6 text-[18px] leading-[25.2px] font-medium md:hidden">Criar conta</button>
      </div>
      <div class="flex justify-between items-center p-6">
        <LogoApp />
        <button class="text-[#0761E2] py-5 px-6 text-[18px] leading-[25.2px] font-medium hidden md:block">Criar conta</button>
      </div>
      <div class="flex flex-col p-6">
        <h2 class="text-[#0E0E0E] dark:text-[#EDEDED] text-[32px] leading-[44.8px] font-semibold">Boas-vindas!</h2>
        <h5 class="text-[#585858] dark:text-[#909090] text-[18px] leading-[25.2px] font-medium">Entre utilizando uma das opções abaixo</h5>
      </div>
      <div class="flex justify-between items-center md:space-x-6 p-6">
        <ButtonDefault class="hidden md:flex" >
          <IconToolzz />
        </ButtonDefault>
        <ButtonDefault class="md:hidden" >
          <IconGoogle />
        </ButtonDefault>
        <ButtonDefault >
          <IconFacebook />
        </ButtonDefault>
        <ButtonDefault >
          <IconICloud />
        </ButtonDefault>
        <ButtonDefault >
          <IconTwitter />
        </ButtonDefault>
      </div>
      <div class="flex justify-between items-center p-6">
          <div class="border-t border-black dark:border-white flex-grow opacity-10"></div>
          <div class="mx-4 text-[18px] leading-[27px] text-[#585858] dark:text-[#909090] font-normal">OU</div>
          <div class="border-t border-black dark:border-white flex-grow opacity-10"></div>
      </div>
      <form @submit.prevent="submitForm" class="flex flex-col justify-between p-6 space-y-6">
        <div class="flex flex-col">
          <label class="text-[16px] leading-[22.4px] text-[#0E0E0E] dark:text-[#EDEDED] font-normal mb-2">Usuário</label>
          <div class="relative w-full">
            <span class="absolute inset-y-0 left-0 flex items-center pl-3">
              <IconUserInput />
            </span>
            <input v-model="email" type="text" class="p-[16px] pl-[38px] rounded-lg border border-[#6A6A6A] dark:border-[#5C5C5C] dark:bg-transparent text-[#585858] dark:text-[#909090] text-[16px] leading-[24px] w-full h-[48px] focus:outline-0">
          </div>
        </div>
        <div class="flex flex-col">
          <label class="text-[16px] leading-[22.4px] text-[#0E0E0E] dark:text-[#EDEDED] font-normal mb-2">Senha</label>
          <div class="relative w-full">
            <span class="absolute inset-y-0 left-0 flex items-center pl-3">
              <IconPasswordInput />
            </span>
            <input v-model="password" type="password" class="p-[16px] pl-[38px] rounded-lg border border-[#6A6A6A] dark:border-[#5C5C5C] dark:bg-transparent text-[#585858] dark:text-[#909090] text-[16px] leading-[24px] w-full h-[48px] focus:outline-0">
          </div>
        </div>
        <div class="flex space-x-3 items-center">
          <input type="checkbox" class="w-[20px] h-[20px] appearance-none dark:bg-transparent dark:border dark:border-[#5C5C5C] dark:checked:bg-[#0761E2] " >
          <label class="text-[14px] leading-[16.94px] text-[#0E0E0E] dark:text-[#EDEDED] font-medium">Manter conectado</label>
        </div>
        <div class="flex justify-center items-center flex-col">
          <HCaptchaDemo />
        </div>
        <div class="flex justify-center items-center">
          <button type="submit" class="flex justify-center items-center space-x-2 px-4 py-3 rounded-lg bg-[#0761E2] w-full">
            <IconLoginButton />
            <p class="text-white text-[18px] leading-[25.2px]">Entrar</p>
          </button>
        </div>
      </form>
      <div class="flex p-6 justify-center items-center text-[16px] leading-[22.4px] font-normal space-x-1">
        <p class="text-[585858] dark:text-[#EDEDED]">Esqueceu sua senha?</p>
        <a class="md:text-[#0761E2] md:dark:text-[#0761E2] text-[#0E0E0E] dark:text-[#EDEDED] font-bold md:font-normal" href="#">Recuperar senha</a>
      </div>
    </div>
  </div>
</template>

<script setup>
import LogoApp from '@/components/LogoApp.vue'
import IconToolzz from '@/components/icons/IconToolzz.vue';
import IconFacebook from '@/components/icons/IconFacebook.vue';
import IconICloud from '@/components/icons/IconICloud.vue';
import IconTwitter from '@/components/icons/IconTwitter.vue';
import IconUserInput from '@/components/icons/IconUserInput.vue';
import IconPasswordInput from '@/components/icons/IconPasswordInput.vue';
import HCaptchaDemo from '@/components/HCaptchaDemo.vue';
import IconLoginButton from '@/components/icons/IconLoginButton.vue'
import ButtonDefault from '@/components/ButtonDefault.vue';
import IconBackButton from '@/components/icons/IconBackButton.vue';
import IconGoogle from '@/components/icons/IconGoogle.vue';
import Slider from '@/components/Slider.vue';

import { ref } from 'vue';
import axios from '@/plugins/axios';
import { useRouter } from 'vue-router';

const router = useRouter();
const email = ref('');
const password = ref('');

const submitForm = async () => {
  try {
    const response = await axios.post('/login', { email: email.value, password: password.value });
    const token = response.data.token;
    
    localStorage.setItem('token', token);
    
    console.log('Login bem-sucedido');

    router.push('/');
  } catch (error) {
    if (error.response) {
      console.error('Erro ao tentar fazer login:', error.response.data.message);
    } else {
      console.error('Erro ao tentar fazer login:', error.message);
    }
  }
};

</script>