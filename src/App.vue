<script setup>
import { ref } from 'vue';
const count = ref(0)
const nama = ref("")


const gambar1 = "/public/favicon.ico"
const gambar2 = "/src/assets/logo.svg"

const gambar = ref(gambar1)
const altText = ref("Gambar Pertama")

const ubahGambar = () =>{
  if(gambar.value === gambar1){
    gambar.value =gambar2
    altText.value = "Gambar Kedua"
  }else{
    gambar.value = gambar1
    altText.value = "Gambar pertama"
  }
}

const loggedIn = ref(false)

const login = () =>{
  loggedIn.value = true
}

const logOut = () => {
  loggedIn.value=false
}

</script>

<template>
<div>{{ count }}</div>
<div>Halo,{{ nama }}</div>

<div>
  <label for="name">Input Nama :</label>
  <input type="text" v-model="nama" placeholder="Tuliskan nama anda">
</div>


<div>
  <button @click="count++">
    Count
  </button>
</div>

<div>
  <h1>{{ altText }}</h1>
  <img :src="gambar" :alt="altText" width="100px">
  <button @click="ubahGambar">Switch</button>
</div>

<div>
  <h1>V-if dan v-else</h1>
  <p v-if="loggedIn">
    Berhasil Login
    <img src="/src//assets/logo.svg" alt="" width="100px">
    <button @click="logOut">LogOut</button>
  </p>
  <p v-else>
    Login Dulu
    <button @click="login">Login</button>
  </p>
</div>

</template>

<style scoped>

</style>
