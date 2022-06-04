<template>
 <div class="px-4 sm:px-6 lg:px-8">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-xl font-semibold text-gray-900">Empresa</h1>
        <p class="mt-2 text-sm text-gray-700">Lista de Enpresas cadastros no sistema.</p>
      </div>
     
    </div>
    <div class="mt-8 flex flex-col">
      <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle md:px-6 lg:px-8">
          <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 md:rounded-lg">
            <table class="min-w-full divide-y divide-gray-300">
              <thead class="bg-gray-50">
                <tr>
                  <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-6">Nome</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">numbeEmployees</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">country</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">category</th>
                
                   
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200 bg-white">
                <tr v-for="empresa in empresa" :key="empresa.id">
                  <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-6">{{ empresa.name }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ empresa.numbeEmployees}}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ empresa.country }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ empresa.category}}</td>
                  
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>



</template>


<script>

import Empresa from '../../service/empresas';

export default {
  name: 'EnpresaApp',
  
    data() {
        return {
        empresa: [],
        }
    },

  mounted() {
    Empresa.listar().then(response => {
      this.empresa = response.data;
      console.log(response.data);
    });
  }
    
  
  
  
}


    
</script>

