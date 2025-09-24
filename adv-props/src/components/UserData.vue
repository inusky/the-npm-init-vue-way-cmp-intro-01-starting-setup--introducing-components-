<!-- Binding all Props
There is another built-in feature/ behavior related to props.
If you have this component: -->

<script setup lang="ts">
const props = defineProps<{ firstname: string; lastname?: string }>()
</script>

<template>
  <h2>{{ props.firstname }} {{ props.lastname ? props.lastname : '' }}</h2>
</template>
