<template>
  <div style="padding: 20px">
    <!-- padding deja una separacion del margen -->
    <h3>Inscribir Alumnos</h3>
    <!-- FORMULARIO -->
    <div style="outline: 1px solid black"  >
      Nombre :{{ nuevoAlumno.nombre }} <br />
      Edad :{{ nuevoAlumno.edad }} <br />
      Promedio :{{ nuevoAlumno.promedio }} <br />
    </div> 

    <br />
    {{ nuevoAlumno }} <br />
    <pre>{{ nuevoAlumno }} </pre>
    <!-- LO ANTERIOR  son distintas maneras de ver los datos que se cargan -->
    <label for="">Nombre</label> <br />
    <input v-model="nuevoAlumno.nombre" type="text" /> <br /><br />
    <!--  Debo ingresar los datos, por lo que debo crear una -->
    <!-- nueva variable,(nuevo alumno), ¿como vamos a vincular-->
    <label for="">Edad</label><br />
    <!-- ha esta variable con los campos de ingreso del formulario?,-->
    <input v-model="nuevoAlumno.edad" type="text" /><br /><br />
    <!-- lo vamos hacer con otra directiva de nuxt que es  (v-model) -->

    <label for="">promedio</label> <br />
    <input v-model="nuevoAlumno.promedio" type="text" />
    <!-- <button @click="alumnos.push(nuevoAlumno)" >Agregar</button>  push se usa para poner un nuevo elemento en el array -->
    <button @click="agregarNuevosAlumnos()">Agregar</button>
    <br />
    <h3>Alumnado :</h3>
    <!-- TABLA -->
    <table border="1">
      <tr>
        <!-- tr es una fila,en este caso tiene los nombres de las columnas -->
        <th>#</th>
        <th>Nombre</th>
        <th>Edad</th>
        <th>Promedio</th>
      </tr>
      <tr v-for="(alumno, index) in alumnos" :key="'alumno' + index">
        <!-- en esta fila pongo los datos <td> -->
        <td>{{ index }}</td>
        <td>{{ alumno.nombre }}</td>
        <td>{{ alumno.edad }}</td>
        <td>{{ alumno.promedio }}</td>
      </tr>
    </table>
 

  </div>

</template>

<script>
export default {
  data() {
    return {
      nuevoAlumno: {
        nombre: "",
        edad: null,
        promedio: null,
      },
      alumnos: [
        /*           {
                nombre: "Pedro",
                edad: 25,
                promedio: 8.7
            },
             {
                nombre: "Luis",
                edad: 20,
                promedio:7.7
            },
             {
                nombre: "Ana",
                edad: 19,
                promedio: 6.7
            },                       */
      ],
    }; //return lleva ;//
  }, // methods va FUERA del DATA//
mounted() {
  this. alumnos = JSON.parse (window.localStorage.getItem("alumnado"));
   
    // el mounted es un gancho que lo aciva nuxt, tomando los datos de localstorage y los vuelve a  cargar cuando inicia la pagina 
  },  
  methods: {
    agregarNuevosAlumnos() {
      //PRIMERA FORMA
      //const nuevoAlumnoCopy = JSON.parse(JSON.stringify(this.nuevoAlumno)); 
     const { ...nuevoAlumnoCopy } = this.nuevoAlumno; //SEGUNDA FORMA DE SOLUCIONAR, le pongo {} porque es un objeto
      this.alumnos.push(nuevoAlumnoCopy);
      window.localStorage.setItem("alumnado",JSON.stringify(this.alumnos)); //con esto ingresamos datos a localstorage
       /*const alumno =JSON.parse (window.localStorage.getItem("alumnado"));
       console.log(alumno);*/
       
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
