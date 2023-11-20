<template>
<div>
  <div class="selectBox" :class="show">
    <div class="selectBox__value form-control" @click="toogleSelect">{{ name }}</div>
    <div class="dropdown-menu">
      <a href="#" class="dropdown-item"><input type="text" class="form-control" v-model="search"></a>
      <a href="#" class="dropdown-item" :class="value==item.value?'active':''" v-for="(item, index) in renderOptions" @click="selectOption(index)">{{ item.name }}</a>
    </div>
  </div>
</div>
</template>

<script setup>
import {onMounted, ref, toRef, watch} from "vue";
const emits = defineEmits(['update:modelValue'])
const props = defineProps({
  options: { type: Object, required: false },
  modelValue: { type: String, required: false },
  className: { type: String, default: "form-select", required: false }
});
let value = toRef(props, "modelValue");
let name = ref("Select your option");
let options = toRef(props, "options");
let renderOptions = ref([]);
const show = ref('hide');
const search = ref('')
onMounted(() => {
  renderOptions.value = options.value;
  options.value.forEach((item) => {
    if(item.value == value.value){
      name.value = item.name;
      return false;
    }
  });
});
watch(search, async (newValue, oldValue) => {
  if(newValue == '') renderOptions.value = options.value;
  else {
    renderOptions.value = [];
    options.value.forEach((item) => {
      if(item.name.toLowerCase().match(newValue.toLowerCase())){
        renderOptions.value.push(item);
      }
    });
  }
})
const selectOption = (index) => {
  let selectedOption = renderOptions.value[index];
  value = selectedOption.value;
  name.value = selectedOption.name;
  emits('update:modelValue', value.value);
  show.value = 'hide';
  search.value = '';
};

const toogleSelect = () => {
  show.value = show.value == 'show'?'hide':'show';
}
</script>

<style scoped>

.selectBox {
  position: relative;
  cursor: pointer;
}
.selectBox__value {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  display: block;
}
.selectBox:after {
  position: absolute;
  right: 12px;
  top: 50%;
  transform: translateY(-50%) rotate(0deg);
  transition: all 0.2s ease-in-out;
  content: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='14.001' height='8.165' viewBox='0 0 14.001 8.165'%3E%3Cdefs%3E%3Cstyle%3E.a%7Bfill:%23212121;%7D%3C/style%3E%3C/defs%3E%3Cpath class='a' d='M13.861,60.224l-.7-.7a.441.441,0,0,0-.645,0L7,65.036,1.487,59.522a.441.441,0,0,0-.645,0l-.7.7a.441.441,0,0,0,0,.645l6.537,6.538a.441.441,0,0,0,.645,0l6.538-6.538a.442.442,0,0,0,0-.645Z' transform='translate(0 -59.382)'/%3E%3C/svg%3E");
}
.selectBox .dropdown-menu {
  transition: all 0.1s ease-in-out;
  opacity: 0;
  display: block;
  top: 100%;
  width: 100%;
  max-height: 250px;
  z-index: -1;
  overflow-y: auto;
  transform: translateY(-15%);
  visibility: hidden;
}
.selectBox.show {
  background-color: #fff;
}
.selectBox.show:after {
  transform: translateY(-50%) rotate(180deg);
}
.selectBox.show .dropdown-menu {
  transition: all 0.3s ease-in-out;
  visibility: visible;
  opacity: 1;
  z-index: 1;
  transform: translateY(0);
}

</style>