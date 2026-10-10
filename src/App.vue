<script setup>
import {ref, computed} from 'vue';
const name = 'Contador con Vue3'
// const styleColor = 'color : navy'
// const arrayColores = ['blue', 'green', 'magenta']
// const activo = false
// const arrayFrutas = ['🍉', '🍎', '🍌', '🍒', '🙈','','🍊']
// const objetoFrutas ={
//     name: "Manzana",
//     price: "$1.00",
//     description: "una manzana",
//     id:1,
//   };
// const arrayFrutas = [
//   {
//     name : "Manzana",
//     price: "$1.00",
//     description:"una manzana",
//     stock:0,
//   },
//   {
//     name : "Pera",
//     price: "$2.00",
//     description:"una pera",
//     stock:10,
//   },
//   {
//     name : "Naranja",
//     price: "$3.00",
//     description:"una naranja",
//     stock:20,
//   },
// ];
// const users = [
//   {
//     id:1,
//     name: "Juan",
//     posts: [
//       {id:1,title:"Mi primer post"},
//       {id:2,title:"Mi segundo post"},
//     ]
//   },
//   {
//     id: 2,
//     name: 'Maria',
//     posts: [
//       { id: 3, title: 'Mi tercer post' },
//       { id: 4, title: 'Mi cuarto post' },
//     ]
//   }
// ]
// método - methods
// const handleClick = (message,) =>{
//   console.log(message);
// }
const numbers = ref([])
const counter = ref(0)
const incremento = () =>{
  console.log('aumentar contador')
  counter.value ++
}
const decremento =()=>{
  counter.value --
}
const resetear =()=>{
  counter.value = 0
}

const agregar = () =>{
  numbers.value.push(counter.value)
}

const disabledAdd = computed(()=>{
  const numSearch = numbers.value.find(num => num === counter.value)
  console.log(numSearch)
  if(numSearch === 0) return true;
  return numSearch ? true : false;
})
const classCounter = computed(()=>{
  if (counter.value === 0) {
    return 'text-odd'
  }
  if (counter.value > 0) {
    return 'text-success'
  }
  if (counter.value < 0) {
    return 'text-danger'
  }
})
</script>

<template gap-2>
  <!-- <h2 :style="`color: ${arrayColores[0]}`">soy azul</h2>
  <h2 :style="`color: ${arrayColores[1]}`" v-if="activo">Estoy activo</h2>
  <p :style="`color: ${arrayColores[2]}`" v-else>Estoy inactivo</p>
  <h2 v-show="activo">Estoy activo con v-show</h2>
  <ul>
    <li v-for="(fruta,index) in arrayFrutas" :key="index">{{index}} - {{ fruta }}</li>
  </ul> -->
  <!-- <ul>
    <li v-for="(value,propiedad,index) in objetoFrutas" :key="value">{{ index }} - {{propiedad}} : {{ value }} </li>
  </ul> -->
  <!-- <ul>
    <template v-for="(item) in arrayFrutas" :key="item.name">
      <li v-if="item.stock > 0"> {{ item.name }} - {{ item.price }}</li>
    </template>
  </ul> -->


  <!-- <div>
    <h2>lista de usuarios</h2>
    <ul>
      <template v-for="(user, index) in users" :key="user.id">
        <li>
          <h3>{{index}} - {{ user.name }}</h3>
          <ul>
            <template v-for="(post, postIndex) in user.posts" :key="post.id">
              <li>{{postIndex}} - {{ post.title }}</li>
            </template>
          </ul>
        </li>
      </template>
    </ul>
  </div> -->
  <!-- <button @click.right.prevent="handleClick('texto right')">Activame right </button>
  <button @click.left="handleClick('texto left')">Activame left</button>
  <button @click.middle="handleClick('texto middle')">Activame middle</button> -->
  <div class="container mt-5 text-center">
    <h1 class="text-secondary fw-bold">{{ name.toUpperCase() }}</h1>
    <h2 class="my-3" :class="classCounter">{{ counter }}</h2>
    <div class="d-flex justify-content-center gap-2">
      <button type="button" class="btn btn-primary" @click="decremento" >Disminuir</button>
      <button type="button" class="btn btn-outline-danger btn-sm" @click="resetear">Resetear</button>
      <button type="button" class="btn btn-primary" @click="incremento">Aumentar</button>
      <button type="button" class="btn btn-success" @click="agregar" :disabled="disabledAdd">Agregar</button>
    </div>

    <ul class="list-group list-group-horizontal mt-4 text-primary-emphasis bg-primary-subtle">
      <li class="list-group-item" v-for="(num,index) in numbers" :key="index">{{ num }}</li>
    </ul>
  </div>

</template>



<style>
body{
  background-color: navy;
}
.text-danger {
  color: red;
}

.text-success{
  color: green;
}

.text-odd{
  color: orange;
}
</style>
