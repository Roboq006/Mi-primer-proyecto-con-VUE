<!-- **************************************************** -->

<script setup>
import {ref, computed} from 'vue' //libreria ref y computed
const name = 'vue dinamico';


const counter = ref(0);
const increment = () =>{
  counter.value ++ 
};
const decrement = ()=>{
  counter.value --;
};
const reset = ()=>{
  counter.value = 0;
};

const Agregar = () =>{
  arrayPractica1.value.push(counter.value); //arrayPractica es una variable reactiva, por eso accedemos al valor con "value"

};

const BloquearBtnAdd = computed(()=>{
  const numSearch = arrayPractica1.value.find(num=>num===counter.value) //Existe counter.value dentro del array?
  console.log(numSearch);
  if(numSearch===0) return true
  return numSearch ? true : false; //Si existe el numero es true para bloquear el btn, caso contrario es falso.

  });

const classCounter = computed(()=>{
  if (counter.value === 0){
    return 'zero';
  }
  if (counter.value>0){
    return 'positivo';
  }
  if (counter.value<0){
    return 'negativo';
  }
 
});

const arrayPractica1 = ref([]); //variable reactiva

</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }} js</h1> 
    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="decrement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="Agregar" :disabled="BloquearBtnAdd" class="btn btn-primary">
        Add
      </button>
    </div>
    <br >{{ arrayPractica1 }}
    <ul class="list-group mt-4">
      <li 
          class="list-group-item"
          v-for="(item, index) in arrayPractica1 " 
          :key="item"
      >
          {{ item }}
      </li>
    </ul>  
  </div>

</template>

<style>
h1 {
  color: red;
}

.positivo{
  color:red
}

.negativo{
  color:green
}

.zero{
  color:peru
}

</style>




<!--**************************************************** -->
<!-- <script setup>
import {ref, computed} from 'vue' //libreria ref y computed
const name = 'vue dinamico';


const counter = ref(0);
const increment = () =>{
  counter.value ++ 
};
const decrement = ()=>{
  counter.value --;
};
const reset = ()=>{
  counter.value = 0;
};

const Agregar = () =>{
  arrayPractica1.value.push(counter.value); //arrayPractica es una variable reactiva, por eso accedemos al valor con "value"

};

const BloquearBtnAdd = computed(()=>{
  const numSearch = arrayPractica1.value.find(num=>num===counter.value) //Existe counter.value dentro del array?
  console.log(numSearch);
  if(numSearch===0) return true
  return numSearch ? true : false; //Si existe el numero es true para bloquear el btn, caso contrario es falso.

  });

const classCounter = computed(()=>{
  if (counter.value === 0){
    return 'zero';
  }
  if (counter.value>0){
    return 'positivo';
  }
  if (counter.value<0){
    return 'negativo';
  }
 
});

const arrayPractica1 = ref([]); //variable reactiva

</script>

<template>
   <h1>Hola {{ name.toUpperCase() }} js</h1> 
   <h2 :class="classCounter">{{ counter }}</h2>

  <button @click="increment">Aumentar</button>
  <button @click="decrement">Disminuir</button>
  <button @click="reset">Reset</button>
  <button @click="Agregar" :disabled="BloquearBtnAdd">Add</button>

 
  <br >{{ arrayPractica1 }}
  <ul>
    <li v-for="(item, index) in arrayPractica1 " :key="item"
         >{{ item }}
    </li>
 </ul>  


</template>

<style>
h1 {
  color: red;
}

.positivo{
  color:red
}

.negativo{
  color:green
}

.zero{
  color:peru
}

</style>  -->

<!-- **************************************************** -->

<!-- **************************************************** -->
<!-- <script setup>
import {ref} from 'vue' //de la librearia 'vue' a ref(este paquete tiene el poder de transformar una variable en una referencia reactica)
const name = 'vue dinamico';
// let counter = 0;
const counter = ref(0);//Ahora counter es una variable reactiva, la paso a const porque tiene mejor preformance, pero lo puedes dejar como let, el ref puede acceder a cualquer tipo de valor.
const increment = () =>{
  console.log('aumentar contador');
  counter.value ++ //para acceder al valor de counter, agregamos value, al tranformarlo a reactiva 'vue' devuelve un objeto que tiene la propiedad 'value'
  //counter ++;
  //console.log(counter);
}
//variables reactivas y ref()
</script>

<template>
   <h1>Hola {{ name.toUpperCase() }} js</h1> 
   <h2>{{ counter }}</h2>
  <button @click="increment">Aumentar</button>
</template>

<style>
h1 {
  color: red;
}
</style> 
   -->
<!-- **************************************************** -->

<!-- <script setup>

const name = 'vue dinamico';

//metodo - methods
const handleClick = (message)=>{
  console.log(message)
}
</script>
<template>
   <h1>Hola {{ name.toUpperCase() }} js</h1>
   <button v-on:click.right.prevent="handleClick('texto Right')">
    Activame right</button>
   <button @:click="handleClick('texto Left')">
    Activame left</button>
   <button v-on:click.middle="handleClick('texto Middle')">
   Activame middle</button>
</template>

<style>
h1 {
  color: red;
}
</style> 
   -->


<!-- **************************************************** -->
<!-- <script setup>
const name = 'vue dinamico';

const arrayFrutas = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];
</script>
<template>
   <h1>Hola {{ name.toUpperCase() }} js</h1>
  <ul>
    <template v-for="elemento in arrayFrutas" :key="elemento.name">
      <li v-if="elemento.stock > 0">{{ elemento.name }}-{{ elemento.price }}-stock:{{ elemento.stock }}</li>
    </template>

  </ul>

</template>

<style>
h1 {
  color: red;
}
</style> 
   -->


<!-- **************************************************** -->
<!-- <script setup>
const name = 'vue dinamico';

const arrayFrutas = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }} js</h1>
  <ul>
    <template v-for="item in arrayFrutas" :key="item.name">
      <li v-if="item.stock > 0">{{ item.name }}-{{ item.price }} </li>
    </template>

  </ul>
</template>

<style>
h1 {
  color: red;
}
</style> 
  -->
 
 
  
<!-- **************************************************** -->
 <!-- <script setup>
const name = 'vue dinamico';
const objetoFruta = {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    }


</script>

<template>
  <h1>Hola {{ name.toUpperCase() }} js</h1>
  {{ objetoFruta }}
  <ul>
    <li v-for ="(value,propiedad, index) in objetoFruta" :key="index" >
    {{ index }} - {{ propiedad }}: {{ value }}
    </li>

  
    
  </ul>
  
</template>

<style>
h1 {
  color: red;
}
</style>  -->

<!-- **************************************************** -->
<!-- <script setup>
const name = 'vue dinamico';

const arrayFrutas = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }} js</h1>
  <ul>
    <li v-for="fruta in arrayFrutas" :key="fruta.name" >{{ fruta.name }}-{{ fruta.price }}-{{ fruta.description }}-{{ fruta.stock }}</li>
  </ul>
  
</template>

<style>
h1 {
  color: red;
}
</style>  -->

<!-- **************************************************** -->

<!-- 
<script setup>
const name = 'vue dinamico';
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
</script>


<template>
  <h1>Hola {{ name.toUpperCase() }} js</h1>
    <ul>
        <li
          v-for="(fruta,index) in arrayFrutas "
          :key="index"
          >{{ index}}-{{ fruta}}</li>
    </ul> 


</template>

<style>
h1 {
  color: red;
}
</style> -->

<!-- **************************************************** -->

<!-- <script setup>
const name = 'vue dinamico';
const styleColor  = "color : blue";
const arrayColores = ["blue","red","peru"];
const activo = false;
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }} js</h1>
  <h2>{{ arrayColores }}</h2> 
  <h2 :style="`color : ${ arrayColores[2] }`">Soy Peru</h2>
  <h2>{{ activo ? 'Estoy activo' : 'Estoy Inactivo' }}</h2>
  <h2 v-if ="activo === true">
    <span>Icono</span>
    Estoy activo
  </h2>
  <p v-else-if ="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>

  <h2 v-show="activo">Estoy activo v-show</h2>

</template>



<style>
h1 {
  color: red;
}
</style> -->