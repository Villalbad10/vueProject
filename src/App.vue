<script setup>
import { ref } from 'vue';

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
const handleClick = (sms) => {
  console.log(sms);
}


const contador = ref(0);

const increment = () => {
  contador.value++
}
const disminuir = () => {
  contador.value--
}
const reset = () => contador.value = 0;

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



  <button @click.right.prevent="handleClick('click derecho')">Activar derecho</button>
  <button @click.middle="handleClick('click scroll')">Activar scroll</button>
  <button @click="handleClick('Click izquierdo')">Activar izquierdo</button><br>



  <h2 :class="contador >0 ? 'positivo': 'negative'">Contador {{contador}}</h2>
  <button @click="increment">Incrementar</button>
  <button @click="reset">Reset</button>
  <button @click="disminuir">Decrementar</button>
</template>

<style>
h1 {
  color: blue;
}

.positivo {
  color: green;
}

.negative {
  color: red;
}
</style>