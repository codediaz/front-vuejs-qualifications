<template>
<div class="container">
 <div class="row">
 
      <div class="col-md-12">
      
        <h1>Sistema de titulación  </h1> 

        <div class="row">
          <input type="text" v-model="buscar" class="form-control" placeholder="Ejemplo: 0927020495"/>
          <button type="button" class="btn btn-secondary btn-lg mt-1" function="searchStudent()">Buscar</button>   
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
      <input type="text" class="form-control" disabled />
    </div>
    <div class="col-sm">
      Apellido:
    </div>
    <div class="col-sm">
     <input type="text" class="form-control" disabled/>
    </div>
    <div class="col-sm">
      Titulación:
    </div>
    <div class="col-sm">
     <input type="text" class="form-control" disabled />
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
export default{
  data(){
    return{
      students:[]
    }
  },

  methods:{
    searchStudent(){
      fetch('http://localhost/students/{student}')
      .then(response=>response.json())
      .then((dataResponse)=>{
        console.log(dataResponse)
        this.students=[]
        if(typeof dataResponse[0].succes== "undefined"){
          this.students = dataResponse
        }
      })
      .catch(console.log)
    }
  }

}

</script>
