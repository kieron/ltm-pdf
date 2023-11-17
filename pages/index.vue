<template>
  <div>
    <h1>CSV to PDF Converter</h1>
    <FileUpload />
  </div>
</template>

<script>
import FileUpload from '@/components/FileUpload.vue';

export default {
  components: {
    FileUpload,
  },
};
</script>