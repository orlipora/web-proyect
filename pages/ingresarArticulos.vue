<template>
           <!-- ----MODIICADO 1------ -->
  <div style="padding: 20px">
    <!-- padding deja una separacion del margen -->
    <h3>Ingresar Articulos Nuevos</h3>
    <!-- FORMULARIO -->
  

    <label for="">Nombre</label> <br />
    <input v-model="nuevoArticulo.nombre" type="text" /> <br /><br />
    <!--  Debo ingresar los datos, por lo que debo crear una -->
    <!-- nueva variable,(nuevo alumno), ¿como vamos a vincular-->
    <label for="">Frente</label><br />
    <!-- ha esta variable con los campos de ingreso del formulario?,-->
    <input v-model="nuevoArticulo.frente" type="text" /><br /><br />
    <!-- lo vamos hacer con otra directiva de nuxt que es  (v-model) -->

    <label for="">Tsup</label> <br />
    <input v-model="nuevoArticulo.tsup" type="text" /> <br /><br />

    <label for="">Tinf</label> <br />
    <input v-model="nuevoArticulo.tinf" type="text" /> <br /><br />

    <label for="">Base</label> <br />
    <input v-model="nuevoArticulo.base" type="text" /> <br /><br />

    <label for="">V1</label> <br />
    <input v-model="nuevoArticulo.v1" type="text" /> <br /><br />

    <label for="">V2</label> <br />
    <input v-model="nuevoArticulo.v2" type="text" /> <br /><br />

    <label for="">V3</label> <br />
    <input v-model="nuevoArticulo.v3" type="text" /> <br /><br />

    <label for="">V4</label> <br />
    <input v-model="nuevoArticulo.V4" type="text" /> <br /><br />

    <label for="">Zocalo</label> <br />
    <input v-model="nuevoArticulo.zocalo" type="text" /> <br /><br />

    <label for="">Tor1</label> <br />
    <input v-model="nuevoArticulo.tor1" type="text" /> <br /><br />

    <label for="">Tor2</label> <br />
    <input v-model="nuevoArticulo.tor2" type="text" />
    <!-- <button @click="alumnos.push(nuevoAlumno)" >Agregar</button>  push se usa para poner un nuevo elemento en el array -->

    <button @click="agregarNuevosArticulos()">Agregar</button>
    <br />
    <h2>Articulos</h2>
    <!-- TABLA -->
    <table border="1">
      <tr>
        <!-- tr es una fila,en este caso tiene los nombres de las columnas -->
        <th>#</th>
        <th>Nombre</th>
        <th>Frente</th>
        <th>Tsup</th>
        <th>Tinf</th>
        <th>Base</th>
        <th>V1</th>
        <th>V2</th>
        <th>V3</th>
        <th>V4</th>
        <th>Zocalo</th>
        <th>Tor1</th>
        <th>Tor2</th>
      </tr>
      <tr v-for="(articulo, index) in articulos" :key="'articulo' + index">
        <!-- en esta fila pongo los datos <td> -->
        <td>{{ index }}</td>
        <td>{{ articulo.nombre }}</td>
        <td>{{ articulo.frente }}</td>
        <td>{{ articulo.tsup }}</td>
        <td>{{ articulo.tinf }}</td>
        <td>{{ articulo.base }}</td>
        <td>{{ articulo.v1 }}</td>
        <td>{{ articulo.v2 }}</td>
        <td>{{ articulo.v3 }}</td>
        <td>{{ articulo.v4 }}</td>
        <td>{{ articulo.zocalo }}</td>
        <td>{{ articulo.tor1 }}</td>
        <td>{{ articulo.tor2 }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nuevoArticulo: {
         nombre: "",
          frente: "",
          tsup: "",
          tinf: "",
          base: "",
          v1: "",
          v2: "",
          v3: "",
          v4: "",
          zocalo: "",
          tor1: "",
          tor2: null,
      },
      articulos: [],
    }; //return lleva ;//
  }, // methods va FUERA del DATA//
  mounted() {
    this.articulos = JSON.parse (window.localStorage.getItem("catalogo"));
     //tomamos los datos de localstorage y los volvemos a cargar cuando iniia la pagina 
  },
  methods: {
    agregarNuevosArticulos() {
      //PRIMERA FORMA//
      // const nuevoAlumnoCopy = JSON.parse(JSON.stringify(this.nuevoAlumno)); //
      const { ...nuevoArticuloCopy } = this.nuevoArticulo; //SEGUNDA FORMA DE SOLUCIONAR, le pongo {} porque es un objeto//
      this.articulos.push(nuevoArticuloCopy);
     window.localStorage.setItem("catalogo",JSON.stringify (this.articulos)) // con esto ingresamos datos a localstorage//
      // const alumnos= JSON.parse(window.localStorage.getItem("alumnado"));//
      /*CUANDO TENGA QUE UTILIZAR LAS VARIABLES que estan dentro del (data) por eje. (nombre,edad,agregarNuevosAlumnos) en donde esta el HTML  o sea dentro de las etiq- template ,las coloco como estan (nombre,edad) .Pero si las uso debajo del DATA  o sea dentro del codigo JS le debo agregar la palabra ( this. )  */
      /* PERO SEGUIMOS con la REACTIVIDAD NO DESEADA , pero ya sabemos cual es la linea que no funciona bien ( y pasa porque estamos trabajando con objetos)  y la tenemos dentro de un methods , podemos agregar algo antes para solucionala .Hay dos formas ,la primera
  VA  a ser con un (JSON) lo que hace transforma un objeto (nuevoAlumno) 
   de Js en un STRING ,  JSON.stringify(this.nuevoAlumno)  .Pero yo lo quiero  nuevamente como un  objeto Js , lo hago con  JSON.parse  , parse significa desarmar, desacoplar,
   por lo tanto voy a tener un objeto DASACOPLADO  y soluciono el problema , y a la variable nuevoAlumnoCopy no le pongo el this , porque fue creada dentro de methods
   --- LA SEGUNDA FORMA DE SOLUCIONARLO Y ES GENERALMENTE LA QUE SE UTILIZA ES --
    se hace con el operador REST  que se representa para usarlo con 3 puntos (...) */
      // GANCHOS Y LOCAL STORAGE---------//
      /*AGREGAMOS alumnos al array, pero cuando iniciamos la pag de nuevo se borra todo y empieza de cero, es porue no solo que los datos estan en una memoria volatil,sino que las variables que estan dentro del data ,las esoy seteando en un estado inicial, o sea le estoy diciendo que cuando se inicie la pag ,se creen estas variables con el estado  inicial, que es sin ningun dato. DEBO BUSCAR LA FORMA QUE LOS DATOS CARGADOS NO SE BORREN. ES USANDO EL LOCAL STORAGE, con el comando windows*/
    },
  },
};
</script>

<style></style>
