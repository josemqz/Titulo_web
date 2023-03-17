<script setup>
// import TheWelcome from '../components/TheWelcome.vue'
import SvgCampus from '../components/SvgCampus.vue'

// recibir datos de ocupación actual a partir de BD ?

var ocupaciones = {"rect5002": 20, "rect5026": 10, "rect4780":23, "rect4780-3": 38, "rect4833": 4, "path5040":200}
var maxOcupaciones = {"rect5002": 30, "path5040":150, "rect5026": 12, "rect4780":50, "rect4780-3": 100, "rect4833": 50}

var tasasOcupacion = {};
Object.keys(ocupaciones).map((id) => {
    console.log(`${id}: ocupacion: ${ocupaciones[id]}, maxOcupacion: ${maxOcupaciones[id]}`);
    tasasOcupacion[id] = ocupaciones[id]/maxOcupaciones[id];
});

console.log("\n- - - - - - - \nTasas de ocupacion:")
Object.values(tasasOcupacion).forEach((i) => {  
  console.log(i)
});

</script>

<template> 
  <main>
    <!-- Disminuir enfoque en el texto -->
    <!-- font-size puede definirse a partir de vw :O -->
    <h1>Ocupación de campus San Joaquín</h1>

    <p>Hacer clic en cada área para ver detalles.</p>

    <SvgCampus :tasasOcupacion=tasasOcupacion />
  </main>
</template>

<style scoped>
main{
  text-align: center;
  display: flex;
  flex-direction:column;
  /* grid-template-rows: 1fr 1fr 4fr; */
  align-items: center;
  /* grid-auto-flow: row; */
}
@media (min-width: 1024px) {
  main{
    /* min-height: 80vh; */
    /* display: flex; */
    grid-gap: 2vh;
  }
}
</style>