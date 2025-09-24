<script setup lang="ts">
import { ref } from 'vue'
const emit = defineEmits<{
  (
    e: 'addFriend',
    payload: {
      id: string;
      name: string;
      phone: string;
      email: string;
      isFavorite: boolean;
    },
  ): void
}>()
const username = ref('')
const userPhone = ref('')
const userEmail = ref('')
const userFavorite = ref(false)

function sendSignal() {
  if (!userPhone.value || !userEmail.value) return

  emit('addFriend', {
    id: new Date().toString(),
    name: username.value,
    phone: userPhone.value,
    email: userEmail.value,
    isFavorite: userFavorite.value,
  })
}
</script>

<template>
  <form @submit.prevent="sendSignal">
    <label for="name">Name: </label>
    <input type="text" id="name" placeholder="Your fullname, optional" v-model="username" />
    <br />
    <br />
    <label for="phone">Phone: </label>
    <input type="tel" id="phone" placeholder="Your phone" v-model="userPhone" />
    <br />
    <br />
    <label for="email">Email: </label>
    <input type="email" id="email" placeholder="Your email" v-model="userEmail" />
    <br />
    <br />
    <label for="is-favorite">Is favorite: </label>
    <input type="checkbox" id="is-favorite" v-model="userFavorite" />
    <br />
    <br />
    <button type="submit">Submit here</button>
  </form>
</template>

<style scoped>
#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
</style>
