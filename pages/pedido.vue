<template>
  <div style="padding:20px" >


    <h3 style="color:red  " >PRODUCTOS : ({{productos.length}})  $ {{total}} </h3>
<!-- FORMULARIO PARA LLENAR EL CARRITO -->
 <!--  las etiq- select son una especie de INPUT que me permite seleccionar un valor de una lista desplegada y dentro de ellas uso una etq-  option-->
 
<select @change="resetearCantidad() "  v-model="productoSeleccionado">  <!-- con v-model ato a la variable con la etiq- -->
<!-- <option value="1">Uniforme</option>
<option value="2">Libro A</option>
<option value="3">Diccionario</option> -->
<option disabled value="-1">Selecciona un producto </option>
<option  v-for="producto,index in productos"  :value="index"  :key="producto.id" > {{producto.nombre}} </option>
 </select>


 <input v-if="productoSeleccionado!= -1"   v-model.number ="cantidad" min="1"   type="number" style="width:40px">
 <!--agregar al carrito -->

 <button @click="agregarProducto()" >Agregar</button> 

   <span v-if=" productoSeleccionado!= -1 " >{{productos[productoSeleccionado].frente }} </span>
   
 <br><br>
  Carrito : {{ carrito}}
  </div>

</template>

<script>
export default {
data(){
    return{
        productoSeleccionado:-1,
        cantidad:1,
        productos:[
         
              {
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
        
        }


        ],
        carrito:[

        ],
       };
} ,
computed:{
     total(){
       var total = 0;
       this.carrito.forEach(producto => {
         total = total+ (producto.cantidad)
       });
       return total;
     }
},

methods:{
  resetearCantidad(){
   this.cantidad = 1 ;
  },
  agregarProducto(){
    let producto = this.productos[this.productoSeleccionado];
    producto.cantidad = this.cantidad; //agregamos una llave nueva (cantidad) a los productos//
       this.carrito.push(producto);
  },

},
};
</script>

<style>

</style>