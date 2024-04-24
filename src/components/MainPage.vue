<template>
    <div>
        <form @submit.prevent="addNombre">
            <input v-model="newNombre" required placeholder="Ingrese un nombre">
            <input v-model="newApellido" required placeholder="Ingrese el apellido">
            <button>Crear nombre completo</button>
        </form>
        <div>
            <ol>
                <li v-for="nombre in nombres" :key="nombre.id">
                    <p>{{ nombre.nombre }} {{ nombre.apellido }}</p>
                    <button @click="verEditarNombre(nombre)">Editar</button>
                    <button @click="removeNombre(nombre)">X</button>
                </li>
            </ol>
        </div>
        <div>
            Aqui se editaran los nombres
            <p>{{ nomEditar.nombre }} {{ nomEditar.apellido }}</p>
            <form @submit.prevent="editarNombre">
                <input v-model="newNombre" required placeholder="Nuevo nombre">
                <input v-model="newApellido" required placeholder="Nuevo apellido">
            <button>Editar nombre</button>
        </form>
        </div>
    </div>
</template>

<script>
let id=0
export default{
    data() {
    return {
      newNombre: '',
      newApellido: '',
      verEdicion: false,
      nomEditar: {id:-1,nombre:'',apellido:''},
      nombres: [
        { id: id++, nombre: 'Nombre1', apellido: 'apellido' },
      ]
    }
    },
    methods:{
        addNombre() {
            this.nombres.push({id:id++, nombre: this.newNombre, apellido: this.newApellido})
            this.newName = ''
        },
        verNombres(){
            console.log(this.nombres);
        },
        removeNombre(nombre){
            this.nombres = this.nombres.filter((n) => n!== nombre)
        },
        verEditarNombre(nombre){

            this.nomEditar = nombre
            this.verEdicion = !this.verEdicion
        },
        editarNombre(){
            console.log("Editar")
        }
    }
}
</script>
<style scoped>
    ol{
        text-align: left;
    }   
</style>