<script setup>
 import { ref } from 'vue';
//  const header = ref('🛒 Shopping List App')
const header = ref('App Lista de compras');
const items = ref([
  {id: 1, label: '10 bolillos'},
  {id: 2, label: '1 lata de frijoles'},
  {id: 3, label: '2 lata de atún'}
]);


 //  const items = ref({
//   "item1": { id: 1, label: '10 bolillos' },
//   "item2": { id: 2, label: '1 lata de frijoles' },
//   "item3": { id: 3, label: '2 lata de atún' },
// });

//  const items = ref([
//      {id: 1, label: '10 bolillos'},
//      {id: 2, label: '1 lata de frijoles'},
//      {id: 3, label: '2 lata de atún'}    
// ]);
</script>

<template>
   <h1> <i class="material-icons  Shopping-cart-icon"> local_mall</i>  {{ header }}  </h1>
    <TheWelcome />
    
  <ul>
    <li v-for="{ id, label } in items" v-bind:key="id">
      🔹 {{ label }}
    </li>
  </ul>
   
   
    <!-- <ul>
    <li v-for="({ id, label }, index) in items" v-bind:key="id">
			🔹 -{{ index }}- {{ label }}
		</li>
  </ul> -->
    
    
    <!-- <ul>
        <li v-for="({ id, label }, index) in items" v-bind:key="id">
        🔹 - {{ index }} - {{ label }}
       </li>
    </ul> -->
    
    
<!--     
    <ul>
         <li v-for="{ id, label } in items" v-bind:key="id">🔹 {{ label }}</li>
       </ul>  
    
    <ul>
         <li v-for="item in items" v-bind:key="item.id">🔹 {{item.label}}</li>
    </ul> -->
    
      <!-- <ul>
         <li v-for="item in items">🔹 {{item}}</li>
      </ul> -->
    <!-- <ul>
    <li>10 bolillos</li>
    <li>1 lata de frijoles</li>
    <li>1 lata de atún</li>
  </ul> -->
</template>

<style scoped>
.Shopping-cart-icon{
    font-size: 3rem;
}
</style>
