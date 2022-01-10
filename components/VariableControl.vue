<template>
  <div>
       <h4>Control de  {{titulo}} </h4>
  <button style="color:MediumSeaGreen" @click="valor--" >- Disminuir--</button >
   <span>{{valor}} </span><span> {{unidad}} </span>
   <button style="color:Violet" @click="valor++" >--Aumentar +</button >
      

  </div>
</template>

<script> /*Las etiq- html tienen  atributos o propiedades (style) ,estas etiq- personalizadas tambien ,propiedades  personalizados,en los componentes son llamadas "props"  */
export default {
    props :["titulo","unidad"],
    data(){
        return{
            valor:0
        };
    },

};
</script>

<style>

/*COMO SE CREAN LOS PROPS :
<script>
export default {
  props: {
    title: String
  },

};
</script>
Como ves, se declarara el nombre del prop y seguido se pone su tipo.

Los tipos que puedes declarar son:

String: Para cadenas de texto.
Number: Para números.
Boolean: Para booleanos true/false.
Array: Listas ya sea de tipos básicos como de objetos.
Object: Objetos de javascript.
Date: Tipo fecha de javascript.
Function: Funciones.
Symbol: Símbolos.*/
</style>
