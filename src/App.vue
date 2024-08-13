<script setup>
import ButtonCounter from "./components/ButtonCounter.vue";
import BlogPost from "./components/BlogPost.vue";
import { ref } from "vue";
import PaginacionPost from "./components/PaginacionPost.vue";
import LoadingSpiner from "./components/LoadingSpiner.vue";

const postXpage = 1;
const inicio = ref(0);
const fin = ref(postXpage);
const post = ref([]);
const loading = ref(true);

const favorito = ref([]);

const postFavorito = (Id, Name, Email, Address, Tel, Website, Compañia) => {
  favorito.value = { Id, Name, Email, Address, Tel, Website, Compañia };
};

const next = () => {
  inicio.value = inicio.value + postXpage;
  fin.value = fin.value + postXpage;
};

const preview = () => {
  inicio.value = inicio.value - postXpage;
  fin.value = fin.value - postXpage;
};

fetch("https://jsonplaceholder.typicode.com/users")
  .then((res) => res.json())
  .then((data) => {
    post.value = data;
  })
  .finally(() => {
    setTimeout(() => {
      loading.value = false;
    }, 2000);
  });

// onMounted(async () => {
//   loading.value = true;
//   try {
//     const res = await fetch("https://jsonplaceholder.typicode.com/");
//     post.value = await res.json();
//   } catch (error) {
//     console.log(error);
//   } finally {
//     setTimeout(() => {
//       loading.value = false;
//     }, 2000);
//   }
// });
</script>

<template>
  <!-- <LoadingSpiner :disabled="true" /> -->
  <div class="container">
    <h1 class="pt-2">Empleados de COCA-COLA</h1>
    <div class="col-12 pt-4">
      <PaginacionPost
        class="mb-2"
        @next="next"
        @preview="preview"
        :inicio="inicio"
        :fin="fin"
        :maxLength="post.length"
      />
      <BlogPost
        v-for="elemento of post.slice(inicio, fin)"
        :key="elemento.id"
        :Id="elemento.id"
        :Name="elemento.name"
        :Username="elemento.username"
        :Email="elemento.email"
        :Address="elemento.address.city"
        :Tel="elemento.phone"
        :Website="elemento.website"
        :Compañia="elemento.company.name"
        @postFavorito="postFavorito"
      />
    </div>
  </div>

  <div class="container">
    <div class="row ms-1">
      <h3 class="align-items-start pt-5 fw-bold fs-2">Empleado del mes:</h3>

      <span class="align-items-start pt-1">
        <div class="fw-bold fs-4" v-for="(elemento, key) of favorito" :key="id">
          {{ key }}
          <span>: {{ elemento }} </span>
        </div>
      </span>
    </div>
  </div>
</template>

<style></style>
