<template>
  <div v-if="show" class="px-5">
    <form class="max-w-screen-sm rounded-lg border-2 border-indigo-400 mx-auto mt-14 p-6">
      <div class="mb-6" v-for="item in input" :key="item.name">
        <div class="flex mb-2 items-center">
          <component :is="item.icon" class="w-10 text-indigo-600 p-1"/>
          <label :for="item.type" class="text-lg font-medium text-gray-900">{{item.name}}</label>
        </div>
        <input :type="item.type" :id="item.id" class="bg-indigo-50 border border-indigo-600 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5" required>
      </div>
      <div class="flex items-start mb-6">
        <div class="flex items-center h-5">
          <input id="remember" aria-describedby="remember" type="checkbox" class="w-4 h-4 bg-indigo-50 rounded border border-indigo-600 focus:ring-3 focus:ring-blue-300" required>
        </div>
        <div class="ml-3 text-sm">
          <label for="remember" class="font-medium text-gray-900 dark:text-gray-300">Запомнить меня</label>
        </div>
      </div>
      <button 
        type="submit" class="text-white bg-indigo-900 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        @click="hidden"
      >Войти</button>
    </form>
  </div>
</template>

<script>
import {UserIcon} from '@heroicons/vue/solid'
import {KeyIcon} from '@heroicons/vue/solid'

const input = [
  {
    id: 'login',
    name: 'Логин',
    icon: UserIcon,
    type: 'text'
  },
  {
    id: 'password',
    name: 'Пароль',
    icon: KeyIcon,
    type: 'password'
  },  
]

export default {
  name: 'App',
  emits: {
    'show-block'(){
      return true;
    }
  },
  data() {
    return {
      show: true,
    }
  },
  components: {
    UserIcon,
    KeyIcon,
  },
  methods: {
    hidden() {
      this.show = false;
      this.$emit('show-block'); 
    },
  },
  setup() {
    return {
      input,
    }
  },
}
</script>
