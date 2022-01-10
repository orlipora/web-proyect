<template>
  <div>
    <h4>Control de {{ titulo2 }}</h4>
    <button style="color: MediumSeaGreen" @click="valor2--"> - Disminuir-- </button>

    <span  :class="{warnig: valor2 >20&&valor2<26 ,danger:valor2>=26} " >{{ valor2 }} </span>
   
    <button style="color: Violet" @click="valor2++">--Aumentar +</button>  <BR></BR>

    <h4 v-if="valor2>20 && valor2<26"  style="color:yellow" >CUIDADO ! </h4> 
     <h4 v-show="valor2>=26 "  style="color:red" >CUIDADO  PELIGRO!! </h4> 
  </div>
</template>
<script>
export default {
  props: ["titulo2", "unidad2"],
  data() {
    return {
      valor2: 0,
    };
  },
};
</script>
<style>
.warnig{
    color: gold;
    font-size: 20px;}
    .danger{
        color: red;
        font-size: 30px;
    }
</style>
