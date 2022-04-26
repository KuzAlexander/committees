<template>
    <div v-if="content" class="sm:flex sm:flex-col lg:flex-row p-5">
        <div class="flex flex-col basis-1/6">
            <button class="relative inline-flex w-full items-center justify-center p-0.5 mb-2 mr-2 overflow-hidden text-lg font-medium text-blue-500 rounded-lg group bg-gradient-to-br from-cyan-500 to-blue-500 group-hover:from-cyan-500 group-hover:to-blue-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-cyan-200 dark:focus:ring-cyan-800"
                v-for="btn in buttons"
                :key="btn">
                <span class="relative w-full px-5 py-2.5 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-md group-hover:bg-opacity-0">
                    <component :is="btn.icon" class="h-5 inline-block"/>
                    {{btn.name}}
                </span>
            </button>
            <div class="flex items-center my-3">
                <input type="checkbox">
                <label class="ml-2 leading-5">Несостоявшиеся комитеты</label>
            </div>
            <div class="flex flex-col">
                <p class="font-bold text-xs mb-3">Условные обозначения:</p>
                <p class="text-md text-white p-1 flex justify-center mb-2 rounded-lg"
                    v-for="item in mark"
                    :key="item"
                    :class="item.color"
                    >{{item.name}}
                </p>
            </div>
        </div>
        <div class="basis-5/6 ml-5">
            <vue-cal 
                :disable-views="['years', 'year']"
                active-view="month"
                locale="ru"
                small
            ></vue-cal>
        </div>
    </div>
</template>

<script>
import {CalendarIcon} from '@heroicons/vue/solid'
import {InformationCircleIcon} from '@heroicons/vue/solid'
import {ClockIcon} from '@heroicons/vue/solid'
import {ViewListIcon} from '@heroicons/vue/solid'
import {PencilIcon} from '@heroicons/vue/solid'
import {PencilAltIcon} from '@heroicons/vue/solid'
import {SearchIcon} from '@heroicons/vue/solid'
import VueCal from 'vue-cal'
import 'vue-cal/dist/i18n/ru.js'
import 'vue-cal/dist/vuecal.css'

const buttons = [
    {
        name: 'График комитетов',
        icon: CalendarIcon
    },
    {
        name: 'Занятость переговорных',
        icon: InformationCircleIcon
    },
    {
        name: 'Фактическая занятость',
        icon: ClockIcon
    },
    {
        name: 'Список событий',
        icon: ViewListIcon
    },
    {
        name: 'Добавить разовое событие',
        icon: PencilIcon
    },
    {
        name: 'Добавить комитет',
        icon: PencilAltIcon
    },
    {
        name: 'Найти комитет',
        icon: SearchIcon
    },
]

const mark = [
    {
        name: 'Ввод информации',
        color: 'bg-gray-400'
    },
    {
        name: 'Согласовано',
        color: 'bg-blue-900'
    },
    {
        name: 'Уведомление загружено',
        color: 'bg-green-900'
    },    
    {
        name: 'Материалы загружены',
        color: 'bg-yellow-800'
    },
    {
        name: 'Протокол загруже',
        color: 'bg-orange-700'
    },
    {
        name: 'Перенесено или отменено',
        color: 'bg-yellow-500'
    },
    {
        name: 'На дополнительном согласовании',
        color: 'bg-orange-500'
    },
    {
        name: 'Отказано',
        color: 'bg-red-600'
    },
]

export default {
    props: ['content'],
    data() {
        return {
            
        }
    },
    components: {
        CalendarIcon,
        InformationCircleIcon,
        ClockIcon,
        ViewListIcon,
        PencilIcon,
        PencilAltIcon,
        SearchIcon,
        VueCal,
    },
    setup() {
        return {
            buttons,
            mark,
        }
  },

}
</script>

<style scoped>

</style>