<template>
  <div class="vuepdf">
    <h1>{{ msg }}</h1>
    <div id="pdf">
      <button v-on:click="pdfgen">Generate PDF</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Pdfgen',
  props: {
    msg: String
  },
  mounted() {
    if (document.getElementById('pdfmake')) return;
    var pdfTag = document.createElement("script");
    pdfTag.src = "https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.38/pdfmake.js";
    pdfTag.id = "pdfmake";
    document.getElementsByTagName('head')[0].appendChild(pdfTag);

    if (document.getElementById('vfs')) return;
    var vfsTag = document.createElement("script");
    vfsTag.src = "https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.38/vfs_fonts.js";
    vfsTag.id = "vfs";
    document.getElementsByTagName('head')[0].appendChild(vfsTag);

  },
  methods: {
    pdfgen: function () {
      if (pdfMake.vfs == undefined){// eslint-disable-line no-undef
        var pdfFonts = require('pdfmake/build/vfs_fonts.js');
        pdfMake.vfs = pdfFonts.pdfMake.vfs; // eslint-disable-line no-undef
      }
      var docDefinition = { content: 'This is an sample PDF printed with pdfMake' }
      pdfMake.createPdf(docDefinition).download('optionalName.pdf') // eslint-disable-line no-undef
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
