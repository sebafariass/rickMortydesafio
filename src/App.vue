<!-- Template que  define al componente -->
<template>
  <!--  DIV ÚNICO -->
   <div class="wallpaper">
    <h1 class="titulo">Personajes</h1>
   <div v-for="(p, i) in datos" :key="i">

  <!--  uso v-for permite recorrer el arreglo  y 
    uso directivav-bind con :key para mejorar
     rendimiento en proyectos    -->   

      <personaje :src="p.imagen_inicial" :name="p.nombre_imagen" /> 
       <!-- Llamo al componente "personaje" pidiendo info para mostrar 
       los datos de las variables dadas desde la api-->
    </div>
  </div>
</template>

<script>

import personaje from "./components/Personaje"; // Importando  componente hijo 
export default {

  components: { // aquí tomamos al component personaje
    personaje,
  },
  
  data() { //funcion data retorna info de datos.mouted
    return {
      
      datos: [], /* array de objetos 
      vacíos para guardar el resultado desde la funcion mouted */
    };
  },

  // Función mounted
  mounted() {

    fetch("https://rickandmortyapi.com/api/character")     // hacemos llamado a la api
      .then((respuesta_api) => respuesta_api.json()) //respuesta del llamado a través de json
      .then((json) => {

        let data = json.results; //guardo data de api results

 
          data.slice(0, 14).forEach((resp) => {  
            /* uso slice para generar limite en busqueda de lo solicitado y mediante
             uso forEach para realizar el recorrido y obtener  datos a mostrar.*/

          let nombre_imagen = resp.name;
          let imagen_inicial = resp.image;   
          /*mediante metodo for each, saco datos de la api con la info de
           "name", "image" , para asigarle la variable y luego incorporarlos
           en el arreglo vacio antes hecho.
           */    

          this.datos.push({
            /*// uso metodo push para enviar info de los datos
            buscados, siempre con  !!!!  .this    !!!
            nombrar la  variable 
          */
            nombre_imagen,
            imagen_inicial,
          });
        });
      })
      //Error en llamado a la data
      .catch((err) => {
        console.log(`Error ${err}`);
      });
  },
};
</script>

<!-- Estilo del componente x style.css -->
<style></style>
