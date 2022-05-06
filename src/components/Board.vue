<template>
    <div class="bg-orange-100 rounded p-6 font-sans">
      <div class="flex flex-col md:flex-row items-center justify-between py-4">
        <div class="flex bg-white rounded p-4 max-w-2xl mb-4 md:mb-0">
          <p class="mr-2">30:00</p>
          
          <div class="h-2 bg-gray-200 mt-2 rounded w-64">
            <div class="h-2 rounded-full bg-blue-500" style="width: 80%;"></div>
          </div>

          <p class="ml-2">40:00</p>
        </div>

        <div class="flex items-center mb-4 md:mb-0">
          <ChevronLeftIcon class="h-12 w-12 text-gray-500 hover:text-gray-600 cursor-pointer"/>

          <p class="text-2xl md:text-4xl font-semibold">
            6 Dec - 10 Dec 2021 
          </p>

          <ChevronRightIcon class="h-12 w-12 text-gray-500 hover:text-gray-600 cursor-pointer"/>
        </div>

        <div>
          <Menu as="div" class="relative inline-block text-left">
            <div>
              <MenuButton
                class="inline-flex w-full justify-center bg-white rounded-full border border-gray-200 p-4 text-sm font-semibold text-gray-500 hover:bg-opacity-30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75"
              >
                Work-week view
                <ChevronDownIcon
                  class="ml-2 -mr-1 h-5 w-5 text-violet-200 hover:text-violet-100"
                  aria-hidden="true"
                />
              </MenuButton>
            </div>

            <transition
              enter-active-class="transition duration-100 ease-out"
              enter-from-class="transform scale-95 opacity-0"
              enter-to-class="transform scale-100 opacity-100"
              leave-active-class="transition duration-75 ease-in"
              leave-from-class="transform scale-100 opacity-100"
              leave-to-class="transform scale-95 opacity-0"
            >
              <MenuItems
                class="absolute right-0 mt-2 w-56 origin-top-right divide-y divide-gray-100 rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
              >
                <div class="px-1 py-1">
                  <MenuItem v-slot="{ active }">
                    <button
                      :class="[
                        active ? 'bg-violet-500 text-white' : 'text-gray-900',
                        'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                      ]"
                    >
                    
                      Work week view
                    </button>
                  </MenuItem>
                  <MenuItem v-slot="{ active }">
                    <button
                      :class="[
                        active ? 'bg-violet-500 text-white' : 'text-gray-900',
                        'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                      ]"
                    >
                    
                      Weekend week view
                    </button>
                  </MenuItem>
                </div>
              </MenuItems>
            </transition>
          </Menu>
        </div>
      </div>

      <div class="md:grid md:grid-cols-5 divide-x divide-orange-300 border border-orange-300 h-full rounded">
        <draggable
          class="p-4"
          :list="day.items"
          group="days"
          itemKey="brand"
          :key="day.id"
          v-for="day in days"
        >
        <template #header>
          <div class="flex justify-between">
            <p class="font-semibold">
              {{day.id}}
            </p>

            <span>
              {{day.hours}}:00 <span class="text-orange-600">of</span> 08:00
            </span>
          </div>

          <div class="h-1 bg-gray-200 w-full mt-2 rounded">
              <div class="h-1 rounded-full" :class="day.hours / 8 * 100 == 100 ? 'bg-green-600' : 'bg-blue-600'" :style="`width: ${day.hours / 8 * 100}%`"></div>
          </div>
        </template>

        <template #item="{ element, index }">
          <card :element="element" />
        </template>
      </draggable>
    </div>
  </div>
</template>

<script setup>
import { Menu, MenuButton, MenuItems, MenuItem } from '@headlessui/vue'
import { ChevronDownIcon } from '@heroicons/vue/solid'
</script>

<script>
import draggable from 'vuedraggable'
import Card from "@/components/Card.vue";
import { ChevronLeftIcon, ChevronRightIcon } from '@heroicons/vue/solid';

  export default {
    components: { draggable, Card, ChevronLeftIcon, ChevronRightIcon },

    data() {
      return {
          days: [
            {
              id: '01 Monday',
              items: [
                { 
                  id: 1, 
                  brand: 'Atradius', 
                  ticket: 'IIND-2816', 
                  time: 1 
                },
                { 
                  id: 2, 
                  brand: 'Coca Cola', 
                  ticket: 'IIND-4542', 
                  time: 3 
                },
                { 
                  id: 3,
                  brand: 'Mollie', 
                  ticket: 'IIND-345345', 
                  time: 4 
                },
              ],
              hours: 2
            },
            {
              id: '02 Tuesday',
              items: [
                { 
                  id: 4, 
                  brand: 'Mollie', 
                  ticket: 'IIND-1222', 
                  time: 1 
                },
                { 
                  id: 5, 
                  brand: 'Mollie', 
                  ticket: 'IIND-2345816', 
                  time: 3 
                },
                { 
                  id: 6, 
                  brand: 'Mollie', 
                  ticket: 'IIND-5655', 
                  time: 3 
                },
                { 
                  id: 7, 
                  brand: 'Mollie', 
                  ticket: 'IIND-78888', 
                  time: 4 
                },
                { 
                  id: 8, 
                  brand: 'Atradius', 
                  ticket: 'IIND-5654', 
                  time: 5 
                },
                { 
                  id: 9, 
                  brand: 'Coca Cola', 
                  ticket: 'IIND-4532', 
                  time: 1 
                },
                { 
                  id: 10, 
                  brand: 'Coca Cola', 
                  ticket: 'IIND-45467', 
                  time: 2 
                },
              ],
              hours: 4
            },
            {
              id: '03 Wednesday',
              items: [
                { 
                  id: 11,
                  brand: 'Mollie', 
                  ticket: 'IIND-342357', 
                  time: 3 
                },
                { 
                  id: 12, 
                  brand: 'Mollie', 
                  ticket: 'IIND-75635', 
                  time: 3 
                },
              ],
              hours: 5
            },
            {
              id: '04 Thursday',
              items: [
                { 
                  id: 13, 
                  brand: 'Atradius', 
                  ticket: 'IIND-46753', 
                  time: 3 
                },
                { 
                  id: 14, 
                  brand: 'Coca Cola', 
                  ticket: 'IIND-45321', 
                  time: 3 
                },
                { 
                  id: 15, 
                  brand: 'Mollie', 
                  ticket: 'IIND-23564', 
                  time: 3 
                },
                { 
                  id: 16, 
                  brand: 'Mollie', 
                  ticket: 'IIND-56764', 
                  time: 3 
                },
                { 
                  id: 17, 
                  brand: 'Coca Cola', 
                  ticket: 'IIND-3133', 
                  time: 3 
                },
                { 
                  id: 18, 
                  brand: 'Mollie', 
                  ticket: 'IIND-234425', 
                  time: 3 
                },
                { 
                  id: 19, 
                  brand: 'Coca Cola', 
                  ticket: 'IIND-453453', 
                  time: 3 
                },
                { 
                  id: 20, 
                  brand: 'Atradius', 
                  ticket: 'IIND-345345', 
                  time: 3 
                },
              ],
              hours: 8
            },
            {
              id: '05 Friday',
              items: [
                { 
                  id: 21, 
                  brand: 'Mollie', 
                  ticket: 'IIND-2816', 
                  time: 4 
                },
                { 
                  id: 22,
                  brand: 'Atradius', 
                  ticket: 'IIND-2816', 
                  time: 4 
                },
                { 
                  id: 23, 
                  brand: 'Atradius', 
                  ticket: 'IIND-2816', 
                  time: 4 
                },
                { 
                  id: 24,
                  brand: 'Coca Cola', 
                  ticket: 'IIND-2816', 
                  time: 4 
                },
                { 
                  id: 25,
                  brand: 'Coca Cola', 
                  ticket: 'IIND-2816', 
                  time: 4 
                },
              ],
              hours: 8
            }
          ]
      }
    },

    methods: {
      getComponentData() {
        return {
          wrap: true,
          value: this.activeNames
        };
      }
    }
  }
</script>
