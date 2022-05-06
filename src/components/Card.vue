<template>
    <div class="flex flex-col mt-2 p-2 bg-white border border-orange-300 rounded cursor-pointer select-none">
        <div class="flex items-center justify-between">
            <div class="text-orange-600">
                {{element.brand}}
            </div>

            <CoffeeIcon />
        </div>

        <div class="my-1 break-normal leading-relaxed" :class="{'truncate': !toggle}">
            This is a very long and extensive discription of the work that has text.
            This is a very long and extensive discription of the work that has text.
            This is a very long and extensive discription of the work that has text.
            This is a very long and extensive discription of the work that has text.
            This is a very long and extensive discription of the work that has text.
        </div>

        <div class="flex justify-between mt-1">
            <p class="uppercase underline">
                {{element.ticket}}
            </p>

            <p class="font-semibold text-base text-orange-900">
                {{element.time}}h
            </p>
        </div>

        <div class="flex justify-center p-1 w-full" @click="toggle = !toggle">
            <div>
                <ChevronUpIcon 
                    class="h-6 w-6 text-gray-500 hover:text-gray-600 cursor-pointer" 
                    v-if="toggle" />

                <ChevronDownIcon 
                    class="h-6 w-6 text-gray-500 hover:text-gray-600 cursor-pointer" 
                    v-else />
            </div>
        </div>
    </div>
</template>

<script>
import draggable from 'vuedraggable'
import { ChevronDownIcon, ChevronUpIcon } from '@heroicons/vue/solid'
import CoffeeIcon from '@/icons/Coffee.vue';

  export default {
    components: { draggable, ChevronUpIcon, ChevronDownIcon, CoffeeIcon },

    props: {
        element: {
            type: Object,
            required: true
        }
    },

    data() {
        return {
            toggle: false
        }
    }
  }
</script>
