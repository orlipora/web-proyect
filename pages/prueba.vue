<template>
  <div>
   <variable-contro-2 titulo2="Temperatura" unidad2="ºC"  ></variable-contro-2>
   <variable-control titulo="Humedad" unidad="%"></variable-control>
 

  </div>
</template>

<script>
import VariableContro2 from '~/components/VariableContro2.vue';
import VariableControl from '~/components/VariableControl.vue'; // esto aparece cuando creamos las etiquetas//
export default {
  components: { VariableControl, VariableContro2 },
    data(){
        return{};
    },};
</script>
<style>
/* {
          id: 1,
          nombre: "77001",
          frente: "360x96",
          tsup: "260x100",
          tinf: "260x100",
          base: "256x90",
          v1: "75x45",
          v2: "90x75",
          v3: null,
          v4: null,
          zocalo: "e27",
          tor1: "Rem-3.2x8",
          tor2: "6x5/8",
          stock:1000
        },
        {
          id: 2,
           nombre: "77001-1R",
          frente: "360x96",
          tsup: "260x100",
          tinf: "260x100",
          base: "256x90",
          v1: "75x45",
          v2: "90x75",
          v3: "pol-opal-165x35",
          v4: null,
          zocalo: "e27",
          tor1: "Rem-3.2x8",
          tor2: "6x5/8",
          stock:1000
        },
           {
          id: 3,
          nombre: "77001-2R",
          frente: "360x96",
          tsup: "260x100",
          tinf: "260x100",
          base: "256x90",
          v1: "75x45",
          v2: "90x75",
          v3: "pol-opal-165x50",
          v4: null,
          zocalo: "e27",
          tor1: "Rem-3.2x8",
          tor2: "6x5/8",
          stock:1000
        },
        {
          id: 4,
          nombre: "77005",
          frente: "250x120",
          tsup: "102x95.5",
          tinf: "102x95.5",
          base: "109x118",
          v1: "75x45",
          v2: "72x68",
          v3: null,
          v4: null,
          zocalo: "g9",
          tor1: "6x5/8",
          tor2: "4x5/8",
          stock:1000
        },
         {
          id: 5,
          nombre: "77012",
          frente: "250x120",
          tsup: "102x95.5",
          tinf: "102x95.5",
          base: "109x118",
          v1: "75x45",
          v2: "72x68",
          v3: null,
          v4: null,
          zocalo: "g9",
          tor1: "6x5/8",
          tor2: "4x5/8",
          stock:1000
        },
         {
          id: 6,
          nombre: "77006",
          frente: "250x100",
          tsup: "102x95.5",
          tinf: "102x95.5",
          base: "109x118",
          v1: "75x45",
          v2: "72x68",
          v3: null,
          v4: null,
          zocalo: "gu10",
          tor1: "6x5/8",
          tor2: "4x5/8",
          stock:1000
        },*/
</style>