<template>
  <div class="content">
    <h1>{{ judul }}</h1>
    <p>Pada website tersebut memiliki luas: </p>
    <ul>
      <li>Luas persegi</li>
      <li>Luas Segitiga</li>
      <li>Luas lingkaran</li>
      <li>Luas Trapesium</li>
      <li>Luas layang-layang</li>
      <li>Luas jajar genjang</li>
      <li>Luas belah ketupat</li>
    </ul>
    <p>Pilih luas yang ingin Anda cari</p>
    <div class="grid">
      <input type="text" v-model="luasInput" placeholder="Mau cari luas apa">
      
      <input v-if="luasInput.toLowerCase() === 'persegi'" type="number" v-model.number="sisi1" placeholder="Sisi 1">  
      <input v-if="luasInput.toLowerCase() === 'persegi'" type="number" v-model.number="sisi2" placeholder="Sisi 2">    
      
      <input v-if="luasInput.toLowerCase() === 'segitiga'" type="number" v-model.number="alas" placeholder="Alas">
      <input v-if="luasInput.toLowerCase() === 'segitiga'" type="number" v-model.number="tinggi" placeholder="Tinggi">

      <input v-if="luasInput.toLowerCase() === 'lingkaran'" type="number" v-model.number="r1" placeholder="Jari-jari 1"> 
      <input v-if="luasInput.toLowerCase() === 'lingkaran'" type="number" v-model.number="r2" placeholder="Jari-jari 2"> 

      <input v-if="luasInput.toLowerCase() === 'trapesium'" type="number" v-model.number="alasA" placeholder="Alas A">
      <input v-if="luasInput.toLowerCase() === 'trapesium'" type="number" v-model.number="alasB" placeholder="Alas B">
      <input v-if="luasInput.toLowerCase() === 'trapesium'" type="number" v-model.number="tinggi" placeholder="Tinggi">

      <input v-if="luasInput.toLowerCase() === 'layang-layang'" type="number" v-model.number="d1" placeholder="Diagonal 1"> 
      <input v-if="luasInput.toLowerCase() === 'lingkaran'" type="number" v-model.number="d2" placeholder="Diagonal 2"> 

      <input v-if="luasInput.toLowerCase() === 'jajar genjang'" type="number" v-model.number="alas" placeholder="Alas">
      <input v-if="luasInput.toLowerCase() === 'jajar genjang'" type="number" v-model.number="tinggi" placeholder="Tinggi">

      <input v-if="luasInput.toLowerCase() === 'belah ketupat'" type="number" v-model.number="d1" placeholder="Diagonal 1"> 
      <input v-if="luasInput.toLowerCase() === 'belah ketupat'" type="number" v-model.number="d2" placeholder="Diagonal 2"> 
      
      <button @click="cariLuas">Cari luas</button>
      <p v-if="luasHasil">{{ luasHasil }}</p>
      <p v-if="text">{{ text }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const judul = 'Menghitung Luas Pada Bangun Datar';
const luasInput = ref('');
const luasHasil = ref('');
const sisi1 = ref('');
const sisi2 = ref('');
const alas = ref('');
const tinggi = ref('');
const r1= ref('');
const r2=ref('');
const alasA= ref('');
const alasB= ref('');
const d1=ref('');
const d2=ref('');
const text= ref('')

const cariLuas = () => {
  switch (luasInput.value.toLowerCase()) {
    case 'persegi':
      luasHasil.value = `luas persegi: ${sisi1.value * sisi2.value}`;
      text.value = `Rumus dari persegi L = sisi x sisi`;
      break;
    case 'segitiga':
      luasHasil.value = `Luas segitiga: ${1 / 2 * alas.value * tinggi.value}`;
      text.value =`Rumus dari segitiga L = 1/2 x alas x tinggi`;
      break;
    case 'lingkaran':
      luasHasil.value = `Rumus luas lingkaran: π x ${3.14 * r1.value * r2.value}`;
      text.value = `Rumus dari Lingkarang L = π × r²`;
      break;
    case 'trapesium':
      luasHasil.value = `luas trapesium:${1 / 2 * (alasA.value + alasB.value) * tinggi.value}`;
      text.value = `Rumus dari trapesium L = ½ x (alas a + alas b) x tinggi trapesium`;
      break;
    case 'layang-layang':
      luasHasil.value = `Rumus luas layang-layang: 1/2 x ${1 / 2 * d1.value * d1.value}`;
      text.value = `Rumus dari trapesium L = ½ x diagonal pertama x diagonal kedua`;
      break;
    case 'jajar genjang':
      luasHasil.value = `Rumus luas jajar genjang: (${alas.value * tinggi.value}`;
      text.value = `Rumus dari trapesium L = a x t`;
      break;
    case 'belah ketupat':
      luasHasil.value = `Rumus luas belah ketupat: 1/2 x (${d1.value * d2.value}`;
      text.value = `Rumus dari trapesium  L = 1/2 x d1 x d2`;
      break;
    default:
      luasHasil.value = 'Bangun datar tidak ditemukan';
  }
};
</script>

<style scoped>
.grid {
  display: grid;
}
.grid input,
button {
  margin-bottom: 10px;
  padding: 10px;
  width:50%;
}
</style>