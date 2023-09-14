
<template>
  <main class="wrapper">
    <Form />
    <Result />
  </main>
</template>

<script setup>
import { ref } from "vue";
import Form from "./components/Form.vue";
import Result from "./components/Result.vue";

const validDate = ref(null);
</script>

<style>
.wrapper {
  width: 40rem;
  height: 30rem;
  background-color: var(--white);
  margin: 0 auto;
  padding: 50px;
  border-radius: 20px 20px 30% 20px;
  display: grid;
  grid-template-rows: 1fr 2fr;
}

@media (max-width: 768px) {
  .wrapper {
    width: 70%;
  }
}
</style>