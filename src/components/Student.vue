<template>
<div class="container">
 <div class="row">
 
      <div class="col-md-12">
      
        <h1>Sistema de titulación </h1> 

        <div class="row">
          <input type="text" v-model="student_code" class="form-control" placeholder="Ejemplo: 0927020495"/>
          <span>{{ error  }}</span>
        </div>      
        <div class="row" style="float:right">
           <button type="button"  class="btn btn-secondary btn-lg mt-1" v-on:click ="searchStudents()">Buscar</button>   
        </div>  
                     
 
      </div>
 
    </div>

    <div class="container mt-5">
 
      <div class="row">

          <h1>Datos del estudiante:  </h1> 
      
      </div>
 
    </div>

    <div class="container mt-1">
    <div class="row">
    <div class="col-sm">
     Nombre:
    </div>
    <div class="col-sm">
      <input type="text" class="form-control" :value="name" disabled />
    </div>
    <div class="col-sm">
      Apellido:
    </div>
    <div class="col-sm">
     <input type="text" class="form-control" v-model="lastname" disabled/>
    </div>
    <div class="col-sm">
      Titulación:
    </div>
    <div class="col-sm">
     <input type="text" class="form-control" v-model="topic" disabled />
    </div>
  </div>
</div>
<div class="container mt-5">
 
      <div class="row">

          <h1>Fases: </h1> 
      
      </div>
 
    </div>

    <div class="container mt-1">

    <div class="row">
      <div class="col-4">
        Fase 1:
      </div>
      <div class="col-6" style="grid: block;">
        <input type="number" class="" required> /50
        <button type="button" class="btn btn-success">Enviar</button>
      </div>
    </div>
    <div class="row pt-2">
      <div class="col-4">
        Fase 4:
      </div>
      <div class="col-6" style="grid: block;">
        <input type="number" class="" required> /30
        <button type="button" class="btn btn-success">Enviar</button>
      </div>
    </div>
    <div class="row pt-2">
      <div class="col-4">
        Fase 3:
      </div>
      <div class="col-6" style="grid: block;">
        <input type="number" class="" required> /20
        <button type="button" class="btn btn-success">Enviar</button>
      </div>
    </div>


</div>

</div>

</template>


<script>
import axios from 'axios'
export default{
  data(){
    return{
      students:{},
      student_code:'',
      name: '',
      lastname: '',
      topic:'',
      error: ''
    }
  },

  methods:{
     async searchStudents(){

      try{
        const r = await axios.get(` http://localhost/v1/students/${this.student_code}`)
      

        this.name = r.data.first_name;
        this.lastname = r.data.surname;
        this.topic = r.data.topic;
        this.error = '';

      }
      catch(e){
        this.error = 'Estudiante no encontrado'
        this.name = '';
        this.lastname = '';
        this.topic = '';
      }
      
    },

    /*async Phase1(){
      try {
        const r = await axios.post()
        
      } catch (error) {
        
      }
    },
    async Phase2(){
      try {
        const r = await axios.post()
        
      } catch (error) {
        
      }
    },
    async Phase3(){
      try {
        const r = await axios.post()
        
      } catch (error) {
        
      }
    }*/
  }

}

</script>
