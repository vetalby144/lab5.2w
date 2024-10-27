<script setup lang="ts">
import {ref} from "vue"

interface User {
  firstName: string;
  lastName: string;
  gender: string;
  age: number;
  position: string;
  photo: string;
  hobbies: string[];
}
defineProps({
  userData: Object as User
})
const matureUserCard = ref('mature')
const kidUserCard = ref('kid')
</script>

<template>
  <div v-if="userData" v-bind:class="userData.age > 18 ? matureUserCard : kidUserCard" class="user-card">
    <img class="user-img" v-bind:src="userData.photo" alt="Світлина користувача">
    <div>
      <p>Ім'я: {{ userData.firstName }}</p>
      <p>Прізвище: {{ userData.lastName }}</p>
      <p v-if="userData.age >= 18">Вік: {{ userData.age }}</p>
      <p>Робоча посада: {{ userData.position }}</p>
      <p>Стать: {{ userData.gender }}</p>
      <div v-if="userData.hobbies.length > 0">
        <p>Хобі:</p>
        <ul>
          <li v-for="hobby in userData.hobbies" :key="hobby">{{ hobby }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
.user-card {
  width: 220px;
  border: 6px dotted #222;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.user-card:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}
.user-img {
  width: 100%;
  height: 150px;
  object-fit: cover;
}
.mature {
  background-color: darkslateblue;
}
.kid {
  background-color: darkgreen;
  color: white;
}
</style>
