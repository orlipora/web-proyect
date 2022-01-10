<template>
  <div>
    <h2>VOLVER A EMPEZAR , VAN ++++++</h2>
    <h4>Control de  Caudal </h4>                        <!--  vuelvo ha usar este modo,y no el de las etiquetas -->
 <button @click="caudal--" >--Disminuir---</button >     <!-- personalizadas. poque en ellas no me funciona -->
   <span class="tipografia " :class="{warnig: caudal >5&&caudal<8 ,danger:caudal>=8} " >{{caudal}} </span><span> m3/s </span>           <!-- el  v-if   -->
   <button @click="caudal++" >--Aumentar--</button >

     <h4 v-if="caudal>5 && caudal<8"  style="color:yellow" >CUIDADO ! </h4> 
     <h4 v-show="caudal>=8 "  style="color:red" >CUIDADO  PELIGRO!! </h4> 

   <variable-control titulo="Temperatura" unidad="ºC"> </variable-control> <!--  aqui pongo las propie- personal- "props" -->
    <variable-control titulo="Humedad" unidad="%"> </variable-control>
    <variable-control titulo="Iluminacion" unidad="lumen"> </variable-control>
  </div>

  
</template>

<script>
import VariableControl from "~/components/VariableControl.vue";
export default {
  components: { VariableControl },
  data() {
    return {
      temperatura: 12,
      humedad: 0,
      iluminacion: 0,
      caudal:0
    };
  },
};
</script>
<style>
.tipografia{
 font-family:Georgia;
 font-size: 20px;
}
 .warnig{
  color:gold;
}
.danger{
  color: red;
}

</style>
