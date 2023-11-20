<script setup>
import { ref } from "vue";
import Select from "@/components/Select.vue";
let options = ref([
  {name: "Atlantic", value: "A"},
  {name: "Atlantica", value: "B"},
  {name: "Cat", value: "C"},
  {name: "Catarpillar", value: "D"},
  {name: "Elephant", value: "E"},
  {name: "Elephant nose", value: "F"}
]);
let value = ref("C");
</script>
<template>
  <div class="col-md-6 offset-md-3">
  <form>
    <fieldset>
      <legend>Disabled fieldset example</legend>
      <div class="mb-3">
        <label for="disabledTextInput" class="form-label">Disabled input</label>
        <input type="text" id="disabledTextInput" class="form-control" placeholder="Disabled input">
      </div>
      <div class="mb-3">
        <label for="disabledSelect" class="form-label">Disabled select menu</label>
        <Select :options="options" v-model="value"></Select>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </fieldset>
  </form>
  </div>





</template>

<style scoped>
</style>
