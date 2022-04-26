<template>
  <Popover class="relative bg-indigo-900">
    <div class="mx-auto px-4 sm:px-5">
      <div class="flex justify-between items-center py-2 md:space-x-10">
        <div class="flex justify-start">
          <a href="#" class="flex mr-3 shrink-0">
            <span class="sr-only">Workflow</span>
            <img class="h-8 w-auto sm:h-10 mr-5" src="@/assets/images/logo_size3.png" alt="" />
            <span class="text-white text-lg mr-1 italic font-bold uppercase mt-2">Комитеты</span>
          </a>
        </div>
        <div class="-mr-0 -my-2 lg:hidden">
          <PopoverButton v-if="list" class="bg-white rounded-md p-2 inline-flex items-center justify-center text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500">
            <span class="sr-only">Open menu</span>
            <MenuIcon class="h-6 w-6" aria-hidden="true" />
          </PopoverButton>
        </div>
        <PopoverGroup v-if="list" as="nav" class="hidden lg:flex sm:space-x-5 xl:space-x-10">
          <Popover class="relative" v-slot="{ open }" v-for="element in menu" :key="element.name">
            <PopoverButton :class="[open ? 'text-gray-200' : 'text-white', 'md:text-sm xl:text-lg group inline-flex items-center text-base font-medium hover:text-gray-200']">
              <span>{{element.name}}</span>
              <component :is="element.icon"  :class="[open ? 'text-gray-200' : 'text-white', 'ml-2 h-5 w-5 group-hover:text-gray-200']" aria-hidden="true" />
            </PopoverButton>

            <transition enter-active-class="transition ease-out duration-200" enter-from-class="opacity-0 translate-y-1" enter-to-class="opacity-100 translate-y-0" leave-active-class="transition ease-in duration-150" leave-from-class="opacity-100 translate-y-0" leave-to-class="opacity-0 translate-y-1">
              <PopoverPanel class="absolute z-10 -ml-4 mt-3 transform px-2 w-screen max-w-md sm:px-0 lg:ml-0 lg:left-1/2 lg:-translate-x-1/2">
                <div class="rounded-lg shadow-lg ring-1 ring-black ring-opacity-5 overflow-hidden">
                  <div class="relative grid gap-6 bg-white px-5 py-6 sm:gap-6 sm:p-5">
                    <a v-for="item in element.content" :key="item.name" :href="item.href" class="-m-3 p-3 flex items-start rounded-lg hover:bg-gray-50">
                      <component :is="item.icon" class="flex-shrink-0 h-6 w-6 text-indigo-600" aria-hidden="true" />
                      <div class="ml-4">
                        <p class="text-base font-medium text-gray-900">
                          {{ item.name }}
                        </p>
                      </div>
                    </a>
                  </div>
                </div>
              </PopoverPanel>
            </transition>
          </Popover>
        </PopoverGroup>
        <div v-if="list" class="hidden lg:flex items-center justify-end shrink-0">
          <Popover class="relative" v-slot="{ open }">
            <PopoverButton :class="[open ? 'text-gray-200' : 'text-white', 'md:text-sm xl:text-lg group inline-flex items-center text-base font-medium hover:text-gray-200']">
              <span>Иванов И.И. (1234)</span>
              <ChevronDownIcon :class="[open ? 'text-gray-200' : 'text-white', 'ml-2 h-5 w-5 group-hover:text-gray-200']" aria-hidden="true" />
            </PopoverButton>

            <transition enter-active-class="transition ease-out duration-200" enter-from-class="opacity-0 translate-y-1" enter-to-class="opacity-100 translate-y-0" leave-active-class="transition ease-in duration-150" leave-from-class="opacity-100 translate-y-0" leave-to-class="opacity-0 translate-y-1">
              <PopoverPanel class="absolute z-10 -ml-4 mt-3 transform px-2 w-screen max-w-xs sm:px-0 lg:ml-0 lg:right-0 lg:-translate-x-0">
                <div class="rounded-lg shadow-lg ring-1 ring-black ring-opacity-5 overflow-hidden">
                  <div class="relative grid gap-6 bg-white px-5 py-6 sm:gap-6 sm:p-5">
                    <a v-for="item in user" :key="item.name" :href="item.href" class="-m-3 p-3 flex items-start rounded-lg hover:bg-gray-50">
                      <component :is="item.icon" class="flex-shrink-0 h-6 w-6 text-indigo-600" aria-hidden="true" />
                      <div class="ml-4">
                        <p class="text-base font-medium text-gray-900">
                          {{ item.name }}
                        </p>
                      </div>
                    </a>
                  </div>
                </div>
              </PopoverPanel>
            </transition>
          </Popover>        
        </div>
      </div>
    </div>

    <transition enter-active-class="duration-200 ease-out" enter-from-class="opacity-0 scale-95" enter-to-class="opacity-100 scale-100" leave-active-class="duration-100 ease-in" leave-from-class="opacity-100 scale-100" leave-to-class="opacity-0 scale-95">
      <PopoverPanel focus class="absolute top-0 inset-x-1 p-2 transition transform origin-top-right lg:hidden z-10">
        <div class="rounded-lg shadow-lg ring-1 ring-black ring-opacity-5 bg-indigo-900">
          <div class="pt-5 pb-6 px-5">
            <div class="flex items-center justify-between">
              <div>
                <img class="h-8 w-auto" src="@/assets/images/logo_size3.png" alt="Workflow" />
              </div>
              <div class="-mr-2">
                <PopoverButton class="bg-white rounded-md p-2 inline-flex items-center justify-center text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500">
                  <span class="sr-only">Close menu</span>
                  <XIcon class="h-6 w-6" aria-hidden="true" />
                </PopoverButton>
              </div>
            </div>
            <div class="mt-6">
              <nav class="grid gap-y-8">
                <div class="w-full px-4 pt-16">
                  <div class="w-full p-2 mx-auto bg-white rounded-2xl">
                    <Disclosure v-slot="{ open }" v-for="item in menu" :key="item.name">
                      <DisclosureButton
                        class="flex justify-between w-full px-4 py-2 mb-2 text-sm font-medium text-left bg-indigo-800 rounded-lg hover:bg-indigo-900 focus:outline-none focus-visible:ring focus-visible:ring-purple-500 focus-visible:ring-opacity-75"
                      >
                        <span
                          class="text-xl text-white"
                          >{{item.name}}</span>
                        <ChevronUpIcon
                          :class="open ? 'transform rotate-180' : ''"
                          class="w-5 h-5 text-white"
                        />
                      </DisclosureButton>
                      <DisclosurePanel class="px-4 pt-4 pb-4 text-sm text-gray-500" v-for="el in item.content" :key="el">
                        <a href="#" class="-m-3 p-3 flex items-center rounded-md hover:bg-gray-100">
                          <span class="ml-3 font-medium text-indigo-900 text-lg">
                            {{el.name}}      
                          </span>
                        </a>
                      </DisclosurePanel>
                    </Disclosure>
                    <Disclosure v-slot="{ open }">
                      <DisclosureButton
                        class="flex justify-between w-full px-4 py-2 mb-2 text-sm font-medium text-left bg-indigo-800 rounded-lg hover:bg-indigo-900 focus:outline-none focus-visible:ring focus-visible:ring-purple-500 focus-visible:ring-opacity-75"
                      >
                        <span
                          class="text-xl text-white"
                          >Иванов И.И. (1234)</span>
                        <ChevronUpIcon
                          :class="open ? 'transform rotate-180' : ''"
                          class="w-5 h-5 text-white"
                        />
                      </DisclosureButton>
                      <DisclosurePanel class="px-4 pt-4 pb-4 text-sm text-gray-500" v-for="el in user" :key="el">
                        <a href="#" class="-m-3 p-3 flex items-center rounded-md hover:bg-gray-100">
                          <span class="ml-3 font-medium text-indigo-900 text-lg">
                            {{el.name}}      
                          </span>
                        </a>
                      </DisclosurePanel>
                    </Disclosure>                                     
                  </div>
                </div>                
              </nav>
            </div>
          </div>
        </div>
      </PopoverPanel>
    </transition>
  </Popover>
</template>

<script>
import { Popover, PopoverButton, PopoverGroup, PopoverPanel } from '@headlessui/vue'
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
import {
  ChevronUpIcon,
  ChartBarIcon,
  CursorClickIcon,
  MenuIcon,
  RefreshIcon,
  ShieldCheckIcon,
  ViewGridIcon,
  XIcon,
} from '@heroicons/vue/outline'
import { ChevronDownIcon } from '@heroicons/vue/solid'

const menu = [
  {
    name: 'График',
    icon: ChevronDownIcon,
    content: [
      {
        name: 'На текущий месяц',
        href: '#',
        icon: ChartBarIcon,            
      },
      {
        name: 'Планирование на следующий месяц',
        href: '#',
        icon: CursorClickIcon,
      },    
      { name: 'Архив', description: "Your customers' data will be safe and secure.", href: '#', icon: ShieldCheckIcon },
      {
        name: 'Заполнить по параметрам (на следующий месяц)',
        href: '#',
        icon: ViewGridIcon,
      },
      {
        name: 'Отправить сообщение секретарям',
        href: '#',
        icon: RefreshIcon,
      },
      {
        name: 'Отправить сообщение участникам',
        href: '#',
        icon: RefreshIcon,
      },
      {
        name: 'Производственный календарь',
        href: '#',
        icon: RefreshIcon,
      },
      {
        name: 'Периоды планирования',
        href: '#',
        icon: RefreshIcon,
      },              
    ]
  }, 
  {
    name: 'Справочники',
    icon: ChevronDownIcon,
    content: [
      {
        name: 'Комитеты',
        href: '#',
        icon: ChartBarIcon,
      },
      {
        name: 'Переговорные',
        href: '#',
        icon: CursorClickIcon,
      },
      { name: 'Площадки', href: '#', icon: ShieldCheckIcon },
      {
        name: 'Пользователи',
        href: '#',
        icon: ViewGridIcon,
      },
      {
        name: 'Домены',
        href: '#',
        icon: RefreshIcon,
      },
      {
        name: 'Направления',
        href: '#',
        icon: RefreshIcon,
      },
      {
        name: 'Дивизионы',
        href: '#',
        icon: RefreshIcon,
      },
      {
        name: 'Площадки (для отчетов)',
        href: '#',
        icon: RefreshIcon,
      },      
      {
        name: 'Подразделения',
        href: '#',
        icon: RefreshIcon,
      },   
      {
        name: 'Типы комитетов',
        href: '#',
        icon: RefreshIcon,
      },   
    ]    
  },
  {
    name: 'Отчеты',
    icon: ChevronDownIcon,
    content: [
      {
        name: 'Журнал учета документов',
        href: '#',
        icon: ChartBarIcon,
      },
      {
        name: 'Сводный отчет',
        href: '#',
        icon: CursorClickIcon,
      },
      { name: 'Список уведомлений', href: '#', icon: ShieldCheckIcon },        
    ]
  },
  {
    name: 'СоцКомитеты',
    icon: ChevronDownIcon,
    content: [
      {
        name: 'Формы',
        href: '#',
        icon: ChartBarIcon,
      },
      {
        name: 'Заполнение форм по типу',
        href: '#',
        icon: CursorClickIcon,
      },  
      {
        name: 'История заполнения',
        href: '#',
        icon: CursorClickIcon,
      },          
    ]
  },
  {
    name: 'НР'
  },
]

const user = [
  {
    name: 'Профиль',
    href: '#',
    icon: ChartBarIcon,
  },
  {
    name: 'Выход',
    href: '#',
    icon: CursorClickIcon,
  },
]

export default {
  props: ['list'],
  components: {
    Disclosure, 
    DisclosureButton, 
    DisclosurePanel,
    Popover,
    PopoverButton,
    PopoverGroup,
    PopoverPanel,
    ChevronDownIcon,
    ChevronUpIcon,
    MenuIcon,
    XIcon,
  },
  setup() {
    return {
      menu,
      user,
    }
  },
}
</script>