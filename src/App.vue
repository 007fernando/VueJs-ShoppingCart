<script setup>
// Esta plantilla inicial utiliza SFC Vue 3 <script setup>
// Consulte https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref, computed } from "vue";
const header = ref('App Lista de compras');
const items = ref([
   {id: 1, label: '10 bolillos', purchased: true, highPriority: false},
   {id: 2, label: '1 lata de frijoles', purchased: false, highPriority: true},
   {id: 3, label: '2 lata de atún', purchased: true, highPriority: true}
]);

//funcion que alterna el estado de comprado de un item
const togglePurchased = (item) => {
  // invertir la propiedad purchase
  item.purchased = !item.purchased;
}
// // Creando propiedad computada que invierte items de la lista
// const reversedItems = computed(() => 
// });
// // Creando propiedad computada que invierte items de la lista
// const reversedItems = computed(() => {
//   return items.value.reverse()❌
// });
// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => {
  return [...items.value].reverse(); 
});
const saveItem = () => {
  items.value.push({id: items.value.length + 1, label: newItem.value})
  //borradon el contenido de newItem
  newItem.value = "";
};
const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(false);
const doEdit = (edit) => {
   //alterando la variable "editing"
  editing.value = edit;
  //limpio el input de texto
  newItem.value = "";
  }
  // Creando una propiedad computada
const characterCount = computed(()=>{
  // Toda propiedad computada debe regresar un valor
  return newItem.value.length;
  
</script>

<template>
  <div class="header">
    <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}</h1>
     <button v-if="!editing" @click="doEdit(true)" class="btn btn-primary">Agrear Articulo</button>
    <button v-else @click="doEdit(false)"  class="btn">Cancelar</button>
   

  </div>
  <!-- <a :href="">
   <i>class="material-icons " </i>  
  </a> -->
  <form v-if="editing" v-on:submit.prevent= "saveItem" class="add-item form">
    <!-- Input de Nuevo Articulo -->
    <input v-model.trim="newItem" type="text" placeholder="Ingresar nuevo articulo">
    <!-- Check Boxes -->
    <label>
      <input v-model="newItemHighPriority" 
      type="checkbox">
      Alta Prioridad
    </label>
    {{ newItemHighPriority ? "🔥" : "🧊" }}
    <!-- Boton de UI -->
    <!-- Utilice el atributo :disabled para desactivar el botón cuando newItem esté vacío -->
    <button class="btn btn-primary" :disabled="newItem === ''">Salvar Artículo</button>
    	<!-- Contador -->
  <p class="counter">
    {{ characterCount }} / 200
  </p>
  </form>
  <ul>
    <li v-for="({ id, label, purchased, highPriority },index) in items" 
    v-bind:key="id"
    :class="{strikeout : purchased, priority : highPriority }"
    @click="togglePurchased(items[index])"
    ><script setup>
// import { ref } from 'vue';
// importamos funcion computed
import { ref, computed } from "vue";
const header = ref('App Lista de compras');
const items = ref([
  {id: 1, label: '10 bolillos', purchased:true, highPriority:false},
  {id: 2, label: '1 lata de frijoles',purchased:false,highPriority:true},
  {id: 3, label: '2 lata de atún',purchased:true,highPriority:true}
]);
//Funcion que alterna el estado de comprado de un item
const togglePurchased = (item) =>{
//invertir la propiedad "purchased"
item.purchased =!item.purchased;
}
//Agregando metodo para guardar nuevo articulo en la lista 
const saveItem=() => {
  items.value.push({id: items.value.length + 1, label: newItem.value})
  //Limpiando el contenido de newItem
  newItem.value= "";
};
const newItem= ref('');
const newItemHighPriority= ref(false);
const editing=ref(false);
const doEdit=(edit) =>{
  //Altero la variable "editing"
  editing.value= edit;
  //Limpio el input de texto
  newItem.value="";
};
// Creando una propiedad computada
const characterCount = computed(()=>{
  return newItem.value.length;
  
});
// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => {
  return [...items.value].reverse();
});

</script>

<template>
  <div class="header">
    <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}</h1>
    <button v-if="!editing" @click="doEdit (true)" class="btn btn-primary">Agregar Articulo</button>
    <button v-else @click="doEdit (false)" class="btn">Cancelar</button>
  
  </div>
  
  <!-- <a v-bind:href="newItem">
    <i class="material-icons shopping-cart-icon">link</i>
  </a> -->
  
  <form v-if="editing" v-on:submit.prevent= "saveItem" class="add-item form">
    <!-- Input de Nuevo Articulo -->
    <input  v-model.trim="newItem" type="text" placeholder="Ingresar nuevo articulo">
   <!-- Check Boxes -->
   <label ><input v-model="newItemHighPriority" type="checkbox">
   
    Alta Prioridad
  </label>
      {{newItemHighPriority ?"🔥": "🧊"}}
    
       <!-- Boton de UI -->
   
    <button class="btn btn-primary" :disabled="newItem === ''">Salvar Artículo</button>
</form>
  <ul>
        	<!-- Contador -->
  <p class="counter">
    {{ characterCount }} / 200
  </p>
    <!-- <li v-for="({ id, label, purchased, highPriority }, index) in items"
    v-bind:key="id"
    :class="{strikeout : purchased, priority : highPriority }"
    @click="togglePurchased(items[index])"
    >
      🔹 {{ label }}
  
    </li> -->
    <li 
	v-for="({ id, label, purchased, highPriority }, index) in reversedItems"
  :class="{ strikeout: purchased, priority: highPriority }" 
	@click="togglePurchased(reversedItems[index])" 
  v-bind:key="id">
	  🔹 {{ label }}
</li>
...
  </ul>
  <p v-if="items.length === 0">🥀 Lista de compras vacia 🥀</p>
  <p v-else>🔥Ingrese más Items🔥</p>


</template>

<style scoped>
.shopping-cart-icon{
font-size: 10rem;
}
</style>
       🔹   {{ label }} 
   
	    v-for="({ id, label, purchased, highPriority }, index) in reversedItems"
       :class="{ strikeout: purchased, priority: highPriority }" 
	      @click="togglePurchased(reversedItems[index])" 
        v-bind:key="id">
	         🔹 {{ label }}
</li>
   
  </ul>
  <p v-if="items.length == 0">🥀 Lista de compras Vacia 🥀</p>
  <p v-else>🔥 Ingrese mas Items 🔥</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem; /* Adjust the font-size value as per your desired size */
}
</style>