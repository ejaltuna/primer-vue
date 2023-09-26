<script setup>
import { ref, computed } from 'vue';

const name = " Vue 3 + Vite"
const styleotro = "color:blue;"
const styleotr = "color:peru;"
const colors = ["blue", "red", "green"];
// const activo = false;
// const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
// const jsonFrutas = [
//   {
//     name: "Manzana",
//     price: "$1.00",
//     description: "Una manzana",
//   },
//   {
//     name: "Pera",
//     price: "$2.00",
//     description: "Una pera",
//   },
//   {
//     name: "Naranja",
//     price: "$3.00",
//     description: "Una naranja",
//   },

// ];
// const jsonFruta =
// {
//   name: "Manzana",
//   price: "$1.00",
//   description: "Una manzana",
// }
// const arrayFrut = [
//   {
//     name: "Manzana",
//     price: "$1.00",
//     description: "Una manzana",
//     stock: 0,
//   },
//   {
//     name: "Pera",
//     price: "$2.00",
//     description: "Una pera",
//     stock: 10,
//   },
//   {
//     name: "Naranja",
//     price: "$3.00",
//     description: "Una naranja",
//     stock: 20,
//   },
// ];

// //metodo... 
// const handleClick = (msj) => {
//   console.log(msj);
// }



const contador = ref(0); //variable reactiva para que asi cuando cambie se haga una render
const arrayFavorito = ref([]); //variable reactiva para que asi cuando cambie se haga una render
const handleClickContador = (cant) => {
  // console.log(cant);
  contador.value++;
  // console.log(contador);
}
const handleClickContadordecrement = (cant) => {

  contador.value--;

}
const reset = () => {
  contador.value = 0;
};

const classConuter = computed(() => {
  if (contador.value === 0) {
    return 'zero'
  }
  if (contador.value > 0) {
    return 'positivo'
  }
  if (contador.value < 0) {
    return 'negativo'
  }
})

const classDisable = computed(() => {
  const numSearch = arrayFavorito.value.find(num => num === contador.value)
  // console.log(numSearch);
  // if(numSearch === 0){  return true }
  // return numSearch ? true : false;
  return numSearch || numSearch === 0;
});


const add = () => {
  arrayFavorito.value.push(contador.value);
}

</script>


<template>
  <!--
  <h2 v-bind:style="styleotro">
    Color otro
  </h2>
  <h2 :style="styleotr">
    Color otro
  </h2>
  <span :style="`color:${colors[2]}`">
    soy
  </span>
  <br />
  <span :style="`color:${colors[2]}`">
    {{ activo ? "Estoy Activo" : "Estoy Inactivo" }}
  </span>


  <p v-if="activo">
    Estoy Act
  </p>
  <p v-else="activo === false">
    No Act
  </p>
  <p v-else="!activo">
    No Act
  </p>

  <ul>
    <li v-for="(frutas, index) in arrayFrutas" :key="index">
      {{ index }} {{ frutas }}
    </li>
  </ul>

  <ul>
    <li :key="index" v-for="(Fruta, index) in  jsonFrutas">
      {{ Fruta.name }}
    </li>
  </ul>

  <ul>
    <li v-for="(value, propiedad, index) in jsonFruta" :key="index">
      {{ index }} -> {{ propiedad }}: {{ value }}
    </li>
  </ul> -->

  <!--   
  //metodooo
  <ul>
    <template v-for="item in arrayFrut" :key="item.name">

      <li v-if="item.stock > 0">
        {{ item.name }} - {{ item.description }}
      </li>
    </template>
  </ul> -->

  <!-- 
  // metodos del click en el bottom
  <ul>

    <button v-on:click.right.prevent="handleClick('msj Right')"> Activar right </button>
    <button @click.Left="handleClick('msj Left')"> Activar left</button>
    <button @click.middle="handleClick('msj Middle')"> Activar Middle</button>
  </ul> -->
  <!-- // Contador  -->


  <div class="container p-5 text-center">
    <h1> Inicio de {{ name.toUpperCase() }}</h1>
    <ul class="list-group">
      <li class="list-group-item">
        <!-- <h2> Contador: </h2><h1 :class="contador>=0?'positivo': 'negativo'" >{{ contador }}</h1> -->
        <h2> Contador: </h2>
        <h1 :class="classConuter">{{ contador }}</h1>

      </li>
    </ul>

    <button class="btn btn-success" @click="handleClickContador(1)">
      Increment
    </button>
    <button class=" btn btn-danger" @click="handleClickContadordecrement(1)">
      Decrement
    </button>
    <button class="btn btn-primary" @click="reset()">
      Reset
    </button>
    <button class="btn btn-info" @click="add()" :disabled="classDisable">
      add
    </button>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(num, index) in arrayFavorito" :key="index">
        <h1>
          {{ num }}
        </h1>
      </li>
    </ul>
  </div>
</template>


<style>
.positivo {
  color: green;
}

.negativo {
  color: red;
}

.zero {
  color: peru;
}

h1 {
  color: cadetblue;
}
</style>