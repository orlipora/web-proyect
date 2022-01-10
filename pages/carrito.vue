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
 <input v-if="productoSeleccionado!= -1"   v-model.number ="cantidad" min="1" :max="productos[productoSeleccionado].stock"  type="number" style="width:40px">
 <!--agregar al carrito -->
 <button @click="agregarProducto()" >Agregar</button>  
   <span v-if=" productoSeleccionado!= -1 " >{{productos[productoSeleccionado].precio * cantidad}} </span>
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
                id:1,
                nombre:"Uniforme",
                precio:12.40,
                max: 2,
                stock:150,
            },
            {   
                id:2,
                nombre:"Libro A",
                precio:21.55,
                max: 2,
                stock:20,
            },

             {   
                id:3,
                nombre:"Mapa",
                precio:4.36,
                max: 5,
                stock:100,
            },
              {   
                id:4,
                nombre:"Diccionario",
                precio:18.5,
                max: 2,
                stock:10,
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
         total = total+ (producto.precio*producto.cantidad)
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