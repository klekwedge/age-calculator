<template>
  <div class="container">
    <Form />
  </div>
</template>

<script lang="ts">
import Form from "./components/Form.vue";

export default {
  components: { Form },
  setup() {
    return {};
  },
};
</script>

<style lang="scss" sroped>
.container {
  background-color: #fdfdfd;
  display: flex;
  flex-direction: column;
  width: 600px;
  margin: 1.25rem;
  height: auto;
  padding: 2.5rem;
  border-radius: 1.875rem;
  border-bottom-right-radius: 8.125rem;
}
</style>
