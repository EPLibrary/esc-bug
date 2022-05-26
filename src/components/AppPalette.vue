<!--
  This example requires Tailwind CSS v3.0+

  This example requires some changes to your config:

  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ],
  }
  ```
-->
<template>
  <TransitionRoot :show="computedOpen" as="template" @after-leave="query = ''" appear>
    <Dialog as="div" class="relative z-10" @close="$emit('updateModelValue', false)">
        <div class="fixed inset-0 bg-gray-500 bg-opacity-25 transition-opacity" />

      <div class="fixed inset-0 z-10 overflow-y-auto p-4 sm:p-6 md:p-20">
          <DialogPanel class="h-20 mx-auto max-w-xl transform divide-y divide-gray-100 overflow-hidden rounded-xl bg-white shadow-2xl ring-1 ring-black ring-opacity-5 transition-all">
            <Combobox @update:modelValue="onSelect">
              <div class="relative">
                <ComboboxInput class="border border-gray-200 focus:bg-gray-100 h-12 w-full border-0 bg-transparent pl-11 pr-4 text-gray-800 placeholder-gray-400 focus:ring-0 sm:text-sm" placeholder="Search..." @change="query = $event.target.value" />
              </div>

              <p v-if="query !== '' && filteredPeople.length === 0" class="p-4 text-sm text-gray-500">No people found.</p>
            </Combobox>
          </DialogPanel>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script setup>
import { computed, ref, defineProps, defineEmits } from 'vue'
import {
  Combobox,
  ComboboxInput,
  Dialog,
  DialogPanel,
  TransitionRoot,
} from '@headlessui/vue'

defineEmits(['updateModelValue'])

const props = defineProps(
  {
    open: {
      type: Boolean,
    },
  }
)

let computedOpen = computed(()=>{
  return props.open;
})

const query = ref('')

function onSelect(person) {
  window.location = person.url
}
</script>