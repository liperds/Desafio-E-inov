<template>


  <div class="px-4 sm:px-6 lg:px-8">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-xl font-semibold text-gray-900">Usuários</h1>
        <p class="mt-2 text-sm text-gray-700">Lista de usuários cadastros no sistema.</p>
      </div>
      <div class="mt-4 sm:mt-0 sm:ml-16 sm:flex-none">
        <button type="button" class="inline-flex items-center justify-center rounded-md border border-transparent 
        bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm hover:bg-indigo-700 
        focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 sm:w-auto" @click="creatUser()">
          Novo usuário
        </button>
        <div v-if="form">
          <div class="relative z-10" aria-labelledby="modal-title" role="dialog" aria-modal="true">
            <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>

            <div class="fixed z-10 inset-0 overflow-y-auto">
              <div class="flex items-end sm:items-center justify-center min-h-full p-4 text-center sm:p-0">
                <div
                  class="relative bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:max-w-lg sm:w-full">
                  <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">


                    <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
                      <h3 class="text-lg leading-6 font-medium text-gray-900" id="modal-title">Cadastro/Edição De
                        Usuário</h3>
                      <form class="mt-8 space-y-6" action="#" method="POST">
                        <input type="hidden" name="remember" value="true">
                        <div class="rounded-md shadow-sm -space-y-px">
                          <div>
                            <label for="Nome" class="sr-only">Nome</label>
                            <input v-model="userForm.name" id="Nome" name="Nome" type="text" required
                              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                              placeholder="Nome">
                          </div>
                          <div>
                            <label for="Enpresas" class="sr-only">Enpresas</label>
                            <input v-model="userForm.company" id="Enpresas" name="Enpresas" type="text" required
                              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-md-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                              placeholder="Enpresas">
                          </div>
                          <div>
                            <label for="email" class="sr-only">Email</label>
                            <input v-model="userForm.email" id="email" name="email" type="email" autocomplete="email"
                              required
                              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-md-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                              placeholder="Email">
                          </div>
                          <div>
                            <label for="telefone" class="sr-only">Telefone</label>
                            <input v-model="userForm.tel" id="telefone" name="telefone" type="text"
                              autocomplete="telefone" required
                              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                              placeholder="Telefone">
                              
                          </div>
                         
                        </div>
                        <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
                          <button type="button" @click="addUser(userForm)"
                            class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-indigo-600 text-base font-medium text-white hover:bg-indigo-900 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 sm:ml-3 sm:w-auto sm:text-sm">Enviar</button>
                          <button @click="form = false" type="button"
                            class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm">Cancel</button>
                        </div>
                      </form>
                    </div>

                  </div>
                </div>
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
    <div class="mt-8 flex flex-col">
      <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle md:px-6 lg:px-8">
          <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5 md:rounded-lg">
            <table class="min-w-full divide-y divide-gray-300">
              <thead class="bg-gray-50">
                <tr>
                  <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-6">Nome
                  </th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Empresa</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">E-mail</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Telefone</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">Data de cadastro
                  </th>
                  <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-6">
                    <span class="sr-only">Edit</span>
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200 bg-white">
                <tr v-for="person in users" :key="person.email">
                  <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-6">{{ person.name
                  }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ person.company }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ person.email }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ person.tel }}</td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ person.data }}</td>
                  <td class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-6">
                    <a href="#" class="text-indigo-600 hover:text-indigo-900" @click="editUser(person)">Editar<span
                        class="sr-only">, {{ person.name }}</span></a>
                    <a href="#" class="ml-4 text-indigo-600 hover:text-indigo-900"
                      @click="deleteUser(person)">Excluir<span class="sr-only">, {{
                          person.name
                      }}</span></a>
                  </td>
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

export default {

  name: 'UsersApp',
  data() {

    return {
      form: false,
      users: [
        { name: 'Fulano da Silva', company: 'E-Inov Soluções Tecnológicas', email: 'fulano.silva@example.com', tel: '(85)9 9275-8518', data: '2022-01-05' },
        { name: 'Fulano da Silva 2', company: 'E-Inov Soluções Tecnológicas', email: 'fulano.silva2@example.com', tel: '(85)9 9275-8518', data: '2022-01-16' },
        { name: 'Fulano da Silva 3', company: 'E-Inov Soluções Tecnológicas', email: 'fulano.silva3@example.com', tel: '(85)9 9275-8518', data: '2022-01-27' },
        { name: 'Fulano da Silva 4', company: 'Guest Posts', email: 'fulano.silva4@example.com', tel: '(85)9 9275-8518', data: '2022-02-09' },
        { name: 'Beltrano da Silva', company: 'Guest Posts', email: 'beltrano.silva@example.com', tel: '(85)9 9275-8518', data: '2022-04-27' },
        { name: 'Beltrano da Silva 2', company: 'Guest Posts', email: 'beltrano.silva2@example.com', tel: '(85)9 9275-8518', data: '2022-04-29' },
        { name: 'Beltrano da Silva 3', company: 'Guest Posts', email: 'beltrano.silva3@example.com', tel: '(85)9 9275-8518', data: '2022-05-02' },
        { name: 'Beltrano da Silva 4', company: 'Guest Posts', email: 'beltrano.silva4@example.com', tel: '(85)9 9275-8518', data: '2022-05-27' },
      ]
    }
  },
  methods: {
    creatUser() {
      this.userForm = {
        name: '',
        company: '',
        email: '',
        tel: '',
        data: ''
      }
      this.form = true;
    },


    addUser(userForm) {

      if (this.editing !== true) {
        this.users.push({
          name: userForm.name,
          company: userForm.company,
          email: userForm.email,
          tel: userForm.tel,
          data: userForm.data
        })
      }
      this.userForm = {
        name: '',
        company: '',
        email: '',
        tel: '',
        data: ''
      }
      this.editing = false;
      this.form = false;

    },
    editUser(userForEdit) {
      this.editing = true;
      this.form = true;
      this.userForm = userForEdit;
    },

    deleteUser(userForDelete) {

      this.users = this.users.filter(user => user.email !== userForDelete.email)

    },
    

  }

}





</script>