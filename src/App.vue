<script setup lang="ts">
import { ref } from 'vue'
import FriendContact from './components/FriendContact.vue'
import NewFriend from './components/NewFriend.vue'
const friends = ref([
  {
    id: 'manuel',
    name: 'Manuel Lorenz',
    phone: '0123 45678 90',
    email: 'manuel@localhost.com',
    isFavorite: true,
  },
  {
    id: 'julie',
    name: 'Julie Jones',
    phone: '0987 654421 21',
    email: 'julie@localhost.com',
  },
])

// COMPLEX APPLICATION:
// const userId = ref('')
// const username = ref('')
// const userPhone = ref('')
// const userEmail = ref('')
// const userFavorite = ref('')
// const userRemove = ref('')
// interface Friend {
//   id: string
//   name: string
//   email: string
//   phone: string
//   isFavorite?: string
// }

// const friends = ref<Friend[]>([])

// function addFriend() {
//   if (!userId.value || !userPhone.value || !userEmail.value) return
//   else {
//     friends.value.push({
//       id: userId.value,
//       name: username.value,
//       phone: userPhone.value,
//       email: userEmail.value,
//       isFavorite: userFavorite.value || 'false',
//     })
//   }

//   userId.value = ''
//   username.value = ''
//   userPhone.value = ''
//   userEmail.value = ''
//   userFavorite.value = ''
//   userRemove.value = ''
// }

// function removeFriend() {
//   if (Number(userRemove.value) > friends.value.length) return
//   else if (Number(userRemove.value) <= friends.value.length && Number(userRemove.value) > 0) {
//     friends.value.splice(Number(userRemove.value) - 1, 1)
//   } else return

//   userId.value = ''
//   username.value = ''
//   userPhone.value = ''
//   userEmail.value = ''
//   userFavorite.value = ''
//   userRemove.value = ''
// }

function listenToggle(id: string) {
  const friend = friends.value.find((f) => f.id === id)
  if (friend) {
    friend.isFavorite = !friend.isFavorite
  }
}

function add_friend(friend: {
  id: string
  name: string
  phone: string
  email: string
  isFavorite: boolean
}) {
  friends.value.push(friend)
}
</script>

<template>
  <section>
    <header>
      <h1>My friends</h1>
    </header>
    <NewFriend @add-friend="add_friend" />
    <ul>
      <FriendContact
        v-for="friend in friends"
        :key="friend.id"
        :id="friend.id"
        :name="friend.name"
        :phone="friend.phone"
        :email="friend.email"
        :is-favorite="friend.isFavorite || false"
        @msg-toggle-favorite="listenToggle"
      />
      <!-- COMPLEX APPLICATION: -->
      <!-- <FriendContact
        v-for="friend in friends"
        :key="friend.id"
        :id="friend.id"
        :name="friend.name"
        :phone="friend.phone"
        :email="friend.email"
        :is-favorite="friend.isFavorite"
      /> -->
    </ul>
    <!-- COMPLEX APPLICATION: -->
    <!-- <br />
    <br />
    <label for="id">Id: </label>
    <input type="text" id="id" placeholder="Your first name in lowercase" v-model="userId" />
    <br />
    <br />
    <label for="name">Name: </label>
    <input type="text" id="name" placeholder="Your full name, OPTIONAL" v-model="username" />
    <br />
    <br />
    <label for="phone">Phone: </label>
    <input type="text" id="phone" placeholder="Your mobile number" v-model="userPhone" />
    <br />
    <br />
    <label for="email">Email: </label>
    <input type="text" id="email" placeholder="Your email address" v-model="userEmail" />
    <br />
    <br />
    <label for="favorite">Is your favorite: </label>
    <input type="text" id="favorite" placeholder="true/false, OPTIONAL" v-model="userFavorite" />
    <br />
    <br />
    <button @click="addFriend">Add friend</button>
    <br />
    <br />
    <label for="removeIndex">Remove friend: </label>
    <input
      v-model="userRemove"
      type="number"
      id="removeIndex"
      placeholder="1 - Number of friends"
    />
    <br />
    <br />
    <button :disabled="friends.length === 0" @click="removeFriend">Remove friend</button> -->
  </section>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>
