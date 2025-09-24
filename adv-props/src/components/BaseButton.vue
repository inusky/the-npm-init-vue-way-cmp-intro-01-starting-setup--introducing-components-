<!-- Prop Fallthrough
You can set props (and listen to events) on a component which you haven't registered inside of that component.
For example: -->

<!-- <script setup lang="ts"></script> -->

<template>
  <button>
    <slot></slot>
  </button>
</template>

<script lang="ts">
export default {}
</script>

<style scoped></style>
