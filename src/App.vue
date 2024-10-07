<script setup> //con esto estoy colocando como api composition
 
 import { ref, computed } from "vue";

 const name = " Mundo Vue 3 - MINEDUC!";
 const name2 = "Cristina Paredes B.";
 let counter = ref(0); // Lo convierte en un objeto reactuivo
 const arrayCounter  = ref([]);  // Convierte al arreglo en un arreglo reactivo
 
const increment = () => {
  counter.value++; // estoy incrementando en uno la cvariable
  //console.log(counter.value);
};
 
const decrement = () => { //funcion flecha
    counter.value--;
    //console.log(counter.value);
};

const reset = () => {
    counter.value = 0;
};

const classCounter = computed(() => {
    if (counter.value === 0) {
        return "cero";
    }
    return counter.value > 0 ? "positivo" : "negativo";
});

const add = () => {
    arrayCounter.value.push(counter.value);
};

const blockNumber = computed(() => {
    let  numSearch = arrayCounter.value.find((num) => num === counter.value);
    console.log(numSearch);
    //return numSearch ||   numSearch ===0;
    if (numSearch===0) return true;
    return numSearch ? true: false;
});

</script>

<template>
  <div class="container text-center mt-5">
    <h1>Hola {{ name }}</h1> <br> 
    <h5> {{ name2 }}</h5>
    <br> 
    
    <h2 :class="classCounter">
      {{ counter }}
    </h2>

    <button @click="increment" class="btn btn-success">Incrementar</button>
    <button @click="decrement" class="btn btn-danger">Descrementar</button>
    <button @click="reset" class="btn btn-secondary">Reset</button>

    <button @click="add" :disabled="blockNumber" class="btn btn-primary">Agregar numero</button>
    <h2 class="mt-3">Mis Favoritos</h2>
 
    <ul class="list-group mt-2">
          <li class="list-group-item" v-for="(item, index) in arrayCounter" :key="index">
              {{ item }}
          </li>
      </ul>
    </div>

</template>

<style>
  .negativo {
      color: red;
  }
  .positivo {
      color: green;
  }
  .cero {
      color: coral;
  }
</style>


 
