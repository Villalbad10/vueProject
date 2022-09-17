<script setup>
const name = 'Diego Villalba';
const styleColor = 'color:red';
const arrayColores = ['hola', 'num', 'text'];
//const arrayFrutas = ['banano', 'manzana', 'pera', 'lulo'];
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
const objetoFruta = {
  name: "Fresa",
  price: "$3.00",
  description: "Una Fresa",
  stock: 20,
}
const activo = true;


//metodo
const handleClick = () => {
  console.log('click');
}


</script>

<template>
  <h1>Hola {{name.toUpperCase()}}</h1>
  <h2 :style="styleColor">Perro simon</h2>
  <h3>{{arrayColores}}</h3>
  <h2 v-if="activo"> Estoy activo</h2>
  <h2 v-if="!activo"> Estoy inactivo</h2>

  <ul>
    <li v-for="fruta in arrayFrutas" :key="fruta.name">{{fruta.name}} - {{fruta.price}} - {{fruta.description}}</li>
  </ul>

  <ul>
    <li v-for="(fruta, propiedad, index) in objetoFruta" :key="index">
      {{index}} {{propiedad}} {{fruta}}
    </li>
  </ul>


  <ul>
    <template v-for="item in arrayFrutas" :key="item.name">
      <li v-if="item.stock > 0">
        {{item.name}} - {{item.price}}
      </li>
    </template>
  </ul>



  <button v-on:click="handleClick">Activar</button>
</template>

<style>
h1 {
  color: blue;
}
</style>