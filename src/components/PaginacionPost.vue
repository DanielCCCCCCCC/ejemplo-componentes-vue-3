<script setup>
defineProps(["inicio", "fin", "maxLength"]);

const emit = defineEmits(["next", "preview"]);
</script>

<template>
  <div class="btn-group" role="group" aria-label="Basic example">
    <button
      @click="emit('preview')"
      type="button"
      class="btn btn-outline-dark"
      :disabled="inicio === 0"
    >
      Previus {{ inicio }}
    </button>

    <button
      @click="emit('next')"
      type="button"
      class="btn btn-outline-dark"
      :disabled="fin >= maxLength"
    >
      Next {{ fin }}
    </button>
  </div>
</template>

<button
  class="btn btn-outline-primary"
  @click="emit('postFavorito', title)"
></button>
