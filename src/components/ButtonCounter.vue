<script setup>
import { ref } from "vue";

const count = ref(0);
</script>

<template>
  <button
    @click="
      {
        {
          count++;
        }
      }
    "
  >
     Click me {{ count }}
  </button>

  <button  @click="{ { count = 0; } } " > Reset </button>
</template>

<style>
    .h1{
        color: brown !important;
    }
</style>