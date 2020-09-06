<!-- Template DEL COMPONENTE HIJO-->
<template>

  <div class="contenido">  <!-- DIV ÚNICO -->

  <!-- con :src  logro vincular mis atributos de html en mi modelo -->
  <div class="info_mostrando">
  <img class="imagen" :src="src" />   
  <h2 class="nombre">{{ name }}</h2> 
  </div>
  <!-- uso moustache para interporal texto,
  la etiqueta moustache se remplazará  x el valor de la propiedad y tambien se actualizará
  cada vez que cambie la propiedad name -->
  </div>
</template>

<script>
// Componente personaje
export default {
     
    name: "personaje", // Nombre de componente
    props: {   // Propiedades pasadas de componente padre a componente hijo
    src: String,
    name: String,
  },
};
</script>

<!-- Estilo del componente -->
<style></style>
