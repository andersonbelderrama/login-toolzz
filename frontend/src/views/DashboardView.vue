<template>
    <div>
      <h1>Dashboard</h1>
      <h2>Bem vindo(a) {{ user?.name }}</h2>
      <p>Email: {{ user?.email }}</p>
      <button @click="logout" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded">Sair</button>
    </div>
  </template>
  
<script setup>
import { ref, onMounted } from 'vue';
import axios from '@/plugins/axios';
import { useRouter } from 'vue-router';

const user = ref(null);
const router = useRouter();

const isUserAuthenticated = () => {
  return localStorage.getItem('token') !== null;
};

const fetchUser = async () => {
  if (!isUserAuthenticated()) {
    router.push('/login');
    return;
  }

  try {
    const response = await axios.get('/user', {
      headers: {
        Authorization: `Bearer ${localStorage.getItem('token')}`
      }
    });
    user.value = response.data;
  } catch (error) {
    console.error('Erro ao obter usuário:', error.message);
    router.push('/login');
  }
};

const logout = () => {
  localStorage.removeItem('token');
  console.log('Logout bem-sucedido');
  router.push('/login');
};

onMounted(fetchUser);
</script>