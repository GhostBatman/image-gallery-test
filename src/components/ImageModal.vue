<template>
  <div v-if="image" class="modal">
    <div class="modal-content">
      <span class="close" @click="closeModal"></span>
      <img :src="image.url" :alt="image.title" />
      <p>{{ image.title }}</p>
      <p>{{ image.description }}</p>
      <p>{{ image.date }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
  image: {
    type: Object,
    required: true
  }
});

const emit = defineEmits(['close']);

const closeModal = () => {
  emit('close');
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-content {
  background: white;
  padding: 20px;
  border-radius: 4px;
  text-align: center;
}
.close {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 24px;
  cursor: pointer;

  &::before {
    content: '×';
  }
}
</style>
