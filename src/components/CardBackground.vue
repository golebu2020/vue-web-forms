<template>
  <div class="card">
    <CustomForm />
  </div>
</template>

<script>
import CustomForm from "./CustomForm.vue";

export default {
  components: {
    CustomForm,
  },
};
</script>

<style>
.card {
  background: #fff;
  padding: 20px;
  width: 400px;
  height: fit-content;
  border: none;
  border-radius: 10px;
  box-shadow: 0px 1px 5px 1px rgba(0, 0, 0, 0.12);
  margin-bottom: 20px;
}
</style>
