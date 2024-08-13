<script setup>
// defineProps(["name", "id", "username", "email"]);
defineProps({
  Name: String,
  Id: Number,
  Username: String,
  Email: String,
  Address: Object,
  Tel: String,
  Website: String,
  Compañia: Object,
  body: {
    type: String,
    default: "Sin descripción",
  },
});

const emit = defineEmits(["postFavorito"]);
</script>

<template>
  <div class="card">
    <div class="card-body">
      <h2 class="card-title">
        <p class="fw-bolder">#{{ Id }}- {{ Name }}</p>
      </h2>
      <h4 class="fw-bold">
        UserName:
        <span> {{ Username }} </span>
      </h4>
      <h4 class="fw-bold">
        E-mail:
        <span> {{ Email }}</span>
      </h4>
      <h4 class="fw-bold">
        Address
        <span>{{ Address }}</span>
      </h4>
      <h4 class="fw-bold">
        Tel:
        <span>{{ Tel }}</span>
      </h4>
      <h4 class="fw-bold">
        Website:
        <span>{{ Website }}</span>
      </h4>
      <h4 class="fw-bold">
        Compañia:
        <span>{{ Compañia }}</span>
      </h4>
    </div>

    <button
      class="btn btn-outline-primary"
      @click="
        emit('postFavorito',Id, Name, Email, Address, Tel, Website, Compañia)
      "
    >
      Elegir como empleado del mes
    </button>
  </div>
</template>
;
