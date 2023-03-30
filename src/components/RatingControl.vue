<template>
  <ul>
    <li :class="{ active: modelValue === 'poor' }">
      <button type="button" @click="activeOption('poor')">Poor</button>
    </li>
    <li :class="{ active: modelValue === 'average' }">
      <button type="button" @click="activeOption('average')">Average</button>
    </li>
    <li :class="{ active: modelValue === 'great' }">
      <button type="button" @click="activeOption('great')">Great</button>
    </li>
  </ul>
</template>

<script setup>
import { ref, computed } from 'vue';
const selectedOption = ref(null);
const emits = defineEmits(['update:modelValue']);

const activeOption = (option) => {
  selectedOption.value = option;
  console.log(
    selectedOption.value,
    'function from within the rating component'
  );
  emits('update:modelValue', option);
};

const props = defineProps({
  modelValue: {
    type: String,
    required: false,
  },
});
</script>

<style scoped>
.active {
  background-color: rgb(92, 63, 92);
}

.active button {
  color: white;
}

ul {
  display: flex;
  list-style: none;
  padding: 0;
  margin: 0.5rem 0;
}
li {
  margin: 0 0.5rem;
  border: 1px solid #ccc;
  padding: 0.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  font: inherit;
  padding: 0;
}
</style>
