<template>
    <div>
      <input type="file" @change="handleFileUpload" accept=".csv" />
      <button @click="generatePDF">Generate PDF</button>
    </div>
  </template>
  
  <script>
  import Papa from 'papaparse';
  import pdfMake from 'pdfmake/build/pdfmake';
  import pdfFonts from 'pdfmake/build/vfs_fonts.js'; 
  import { vfs } from 'pdfmake/build/vfs_fonts.js'; // Use the correct export name
  pdfMake.vfs = vfs;

  pdfMake.vfs = pdfFonts.pdfMake.vfs;
  
  export default {
    data() {
      return {
        csvData: null,
      };
    },
    methods: {
      handleFileUpload(event) {
        const file = event.target.files[0];
        if (file) {
          Papa.parse(file, {
            complete: (result) => {
              this.csvData = result.data;
            },
          });
        }
      },
      generatePDF() {
        if (this.csvData) {
          const pdfContent = {
            content: [
              {
                table: {
                  body: [this.csvData],
                },
              },
            ],
          };
  
          pdfMake.createPdf(pdfContent).download('output.pdf');
        }
      },
    },
  };
  </script>
  