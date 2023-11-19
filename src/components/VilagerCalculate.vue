<template>
  <div class="justify-center flex bg-blue-300 items-center h-screen">
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
        Villager 1
      </label>

      <div class="grid grid-cols-2 gap-4">
      <div class="relative">
        <input v-model="vilagerAge1" class="block px-2.5 pb-2.5 pt-4 w-full border text-sm text-gray-900 bg-transparent rounded-lg border-1 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" id="ages1" type="text" placeholder="">
        <label for="ages1" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-2 z-10 origin-[0] bg-white dark:bg-gray-900 px-2 peer-focus:px-2 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 peer-placeholder-shown:top-1/2 peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto start-1"> Ages</label>
      </div>
      <div class="relative">
        <input v-model="vilagerDeath1" class="block px-2.5 pb-2.5 pt-4 w-full border text-sm text-gray-900 bg-transparent rounded-lg border-1 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" id="death1" type="text" placeholder="">
        <label for="death1" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-2 z-10 origin-[0] bg-white dark:bg-gray-900 px-2 peer-focus:px-2 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 peer-placeholder-shown:top-1/2 peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto start-1"> Year of Death</label>
      </div>
</div>
     
      
    </div>
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
        Villager 2
      </label>

      <div class="grid grid-cols-2 gap-4">
      <div class="relative">
        <input v-model="vilagerAge2" class="block px-2.5 pb-2.5 pt-4 w-full border text-sm text-gray-900 bg-transparent rounded-lg border-1 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" id="ages2" type="text" placeholder="">
        <label for="ages2" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-2 z-10 origin-[0] bg-white dark:bg-gray-900 px-2 peer-focus:px-2 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 peer-placeholder-shown:top-1/2 peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto start-1"> Ages</label>
      </div>
      <div class="relative">
        <input v-model="vilagerDeath2" class="block px-2.5 pb-2.5 pt-4 w-full border text-sm text-gray-900 bg-transparent rounded-lg border-1 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer" id="death2" type="text" placeholder="">
        <label for="death2" class="absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-4 scale-75 top-2 z-10 origin-[0] bg-white dark:bg-gray-900 px-2 peer-focus:px-2 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 peer-placeholder-shown:top-1/2 peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4 rtl:peer-focus:translate-x-1/4 rtl:peer-focus:left-auto start-1"> Year of Death</label>
      </div>
</div>
     
      
    </div>
    <div class="flex items-center justify-end">
      <button @click="calculate" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Calculate
      </button>
    </div>
    {{result.data }}
  </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      result : String(),
      vilagerAge1: null,
      vilagerAge2: null,
      vilagerDeath1: null,
      vilagerDeath2: null,
    }
  },
  methods:{
    calculate: async function (){
      try{
      this.result = await axios.get("/sorcerer/calculate",{params : {
        ages:`${this.vilagerAge1},${this.vilagerAge2}`,
        death:`${this.vilagerDeath1},${this.vilagerDeath2}`,
    }})
  }catch(e){
    this.result="error"
  }
    }
  },
  mounted(){
  }
}
</script>
