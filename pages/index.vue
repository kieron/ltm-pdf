<template>
    <div>
      <h1>CSV to PDF Converter</h1>
      <FileUpload />
    </div>
  </template>
  
  <script>
  import FileUpload from '~/components/FileUpload.vue';
  
  export default {
    components: {
      FileUpload,
    },
    head() {
        return {
            title: 'CSV to PDF Converter', // Set the title for the page
        };
    },
  };
  </script>