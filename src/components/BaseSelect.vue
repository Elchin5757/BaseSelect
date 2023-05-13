<script setup lang="ts">
import { type PropType, computed, toRefs } from "vue";
import {
  Listbox,
  ListboxButton,
  ListboxLabel,
  ListboxOption,
  ListboxOptions,
} from "@headlessui/vue";

const emits = defineEmits(["update:modelValue"]);

const props = defineProps({
  modelValue: [String, Number] as PropType<any>,
  label: {
    type: [String, null] as PropType<any>,
    default: "label",
  },
  items: {
    type: Array as PropType<any[]>,
    required: true,
  },
  placeholder: {
    type: String as PropType<string>,
    default: "",
  },
  errorMessage: [String, null] as PropType<any>,
});
toRefs(props);
function changeModalValue(event: any) {
  emits("update:modelValue", event); // previously was `this.$emit('input', title)`
}

const selectedName = computed(() => {
  return props.items.find((item) => item.value === props.modelValue)?.name;
});
</script>

<template>
  <Listbox
    as="div"
    :modelValue="modelValue"
    @update:modelValue="changeModalValue"
  >
    <ListboxLabel class="inline-block mb-1 text-sm font-medium text-gray-900">{{
      label
    }}</ListboxLabel>
    <div class="relative">
      <ListboxButton
        :class="[errorMessage ? 'border-red-500' : 'border-[#8996A2]']"
        class="relative w-full cursor-default rounded-[10px] py-3 px-4 text-left text-[#8996A2] shadow-sm border bg-gray-50 focus:outline-none focus:ring-[#1AA4FF] sm:text-sm sm:leading-6"
      >
        <span class="flex items-center justify-between">
          <span v-if="!modelValue" class="block truncate text-sm leading-6">{{
            placeholder
          }}</span>
          <span
            v-else
            class="block truncate text-sm leading-6 text-[#031633]"
            >{{ selectedName }}</span
          >
          <svg
            width="18"
            height="9"
            viewBox="0 0 18 9"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M16.9201 0.950195L10.4001 7.4702C9.63008 8.2402 8.37008 8.2402 7.60008 7.4702L1.08008 0.950195"
              stroke="currentColor"
              stroke-width="1.5"
              stroke-miterlimit="10"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </span>
      </ListboxButton>

      <transition
        leave-active-class="transition ease-in duration-100"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <ListboxOptions
          class="absolute z-20 mt-1 max-h-56 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none sm:text-sm"
        >
          <ListboxOption
            as="template"
            v-for="person in items"
            :key="person.value"
            :value="person.value"
            v-slot="{ active, selected }"
          >
            <li
              :class="[
                active ? 'bg-[#1AA4FF] text-white' : 'text-[#8996A2]',
                'relative cursor-default select-none py-2 pl-3 pr-9',
              ]"
            >
              <span
                :class="[
                  selected ? 'font-semibold' : 'font-normal',
                  'block truncate',
                ]"
                >{{ person.name }}</span
              >
            </li>
          </ListboxOption>
        </ListboxOptions>
      </transition>
    </div>
    <p class="text-sm text-red-500 mt-1" v-if="errorMessage">
      {{ errorMessage }}
    </p>
  </Listbox>
</template>
