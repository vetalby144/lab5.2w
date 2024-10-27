<script setup lang="ts">
import UserCard from './components/UserCard.vue'
import {computed, ref} from "vue";

const usersToDisplay= ref<User[]>([]);
const genders = ['чоловік', 'жінка'];
const genderOption = ref('');
const sampleUsers: User[] = [
  {
    firstName: "Олена",
    lastName: "Шевченко",
    gender: "Жінка",
    age: 21,
    position: "Програміст",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Читання", "Подорожі", "Малювання"]
  },
  {
    firstName: "Андрій",
    lastName: "Ковальчук",
    gender: "Чоловік",
    age: 40,
    position: "Керівник проектів",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Кулінарія", "Риболовля", "Теніс"]
  },
  {
    firstName: "Максим",
    lastName: "Зеленський",
    gender: "Чоловік",
    age: 28,
    position: "Стажер",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Футбол", "Музика", "Фотографія"]
  },
  {
    firstName: "Наталія",
    lastName: "Кравченко",
    gender: "Жінка",
    age: 15,
    position: "UX Дизайнер",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Йога", "Фотографія", "Подорожі"]
  },
  {
    firstName: "Іван",
    lastName: "Петренко",
    gender: "Чоловік",
    age: 31,
    position: "Аналітик даних",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Велосипед", "Шахи", "Кулінарія"]
  },
  {
    firstName: "Марія",
    lastName: "Василенко",
    gender: "Жінка",
    age: 24,
    position: "Фахівець з маркетингу",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Мода", "Малювання", "Подорожі"]
  },
  {
    firstName: "Олексій",
    lastName: "Гончарук",
    gender: "Чоловік",
    age: 18,
    position: "Веб-розробник",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Кодинг", "Чиназес", "Біг"]
  },
  {
    firstName: "Вікторія",
    lastName: "Бондаренко",
    gender: "Жінка",
    age: 27,
    position: "Копірайтер",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Писання", "Подорожі", "Фотографія"]
  },
  {
    firstName: "Олег",
    lastName: "Дмитренко",
    gender: "Чоловік",
    age: 34,
    position: "Системний адміністратор",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Ігри", "Подорожі", "Кулінарія"]
  },
  {
    firstName: "Юлія",
    lastName: "Мельник",
    gender: "Жінка",
    age: 19,
    position: "Аналітик бізнес-процесів",
    photo: new URL('@/assets/pho.jpg', import.meta.url).href,
    hobbies: ["Йога", "Читання", "Подорожі"]
  }
];

const usersByGender = computed(() => {
  if (genderOption.value) {
    return usersToDisplay.value.filter(u => u.gender.toLowerCase() === genderOption.value);
  }
  return usersToDisplay.value;
});

function displayUsers(){
  usersToDisplay.value = sampleUsers;
}
</script>

<template>
  <main>
    <div class="nav-bar">
      <button v-for="gender in genders" :key="gender" class="btn" @click="genderOption = gender">{{ gender }}</button>
      <button class="btn" @click="genderOption = ''">Всі користувачі</button>
      <button class="btn" @click="displayUsers">Відобразити користувачів</button>
    </div>
    <div class="flex" v-if="usersToDisplay.length > 0">
      <UserCard v-for="user in usersByGender" :key="user" :user-data="user"></UserCard>
    </div>
    <div v-else>
      <p>Список користувачів порожній</p>
    </div>
  </main>
</template>

<style scoped>
.flex {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 25px;
}
</style>
