<script setup lang="ts">
import { ref } from 'vue'
const detailsAreVisible = ref(false)
const props = defineProps<{
  id: string
  name: string
  phone: string
  email: string
  // COMPLEX APPLICATION:
  // isFavorite?: string
  isFavorite: boolean
}>()

// COMPLEX APPLICATION:
// const friendIsFavorite = ref(props.isFavorite ?? 'false')

function toggleDetails() {
  detailsAreVisible.value = !detailsAreVisible.value
}

/* GIVES ERROR - THE PROP IS READ-ONLY:
function toggleFavorite() {
  if (props.isFavorite === '1') {
    props.isFavorite = '0';
  } else {
    props.isFavorite = '1';
  }
} */

const emit = defineEmits<{
  (e: 'msg-toggle-favorite', payload: string): void
}>()

function toggleFavorite() {
  emit('msg-toggle-favorite', props.id)
}
</script>

<template>
  <li>
    <h2>{{ props.name }} {{ props.isFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ props.phone }}</li>
      <li><strong>Email:</strong> {{ props.email }}</li>
    </ul>
  </li>
</template>

<style scoped></style>
