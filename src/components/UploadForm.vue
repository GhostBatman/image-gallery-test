<template>
  <div class="upload-form">
    <input type="file" @change="onFileChange" multiple accept="image/png, image/gif, image/jpeg"  />
  </div>
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['files-selected']);

const onFileChange = (event) => {
  const files = event.target.files;
  emit('files-selected', files);
};
</script>

<style scoped>
.upload-form {
  margin-bottom: 20px;
}
</style>
