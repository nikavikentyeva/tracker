<template>
  <div class="flex gap-2">
    <BaseButton @click="emit('select', null)">
      <XMarkIcon class="h-8"/>
    </BaseButton>
    <select
      class="w-full truncate rounded bg-gray-100 py-1 px-2 text-2xl"
      @change="emit('select', +$event.target.value)"
    >
      <option :selected="isNotSelected" disabled value="">{{ placeholder }}</option>
      <option
        v-for="{value, label} in options"
        :key="value"
        :value="value"
        :selected="value === selected"
      >

        {{ label }}

      </option>
    </select>
  </div>
</template>

<script setup>
import BaseButton from './BaseButton.vue'
import { XMarkIcon } from '@heroicons/vue/24/outline'
import { computed, defineProps } from 'vue'
import { validateSelectOptions, isUndefinedOrNull, isNumberOrNull } from '../validators'

const emit = defineEmits({
  select: isNumberOrNull
 })

const props = defineProps({
  options: {
    type: Array,
    required: true,
    validator: validateSelectOptions
  },
  placeholder: {
    type: String,
    default: 'Rest'
  },
  selected: {
    type: Number,
  }
})

const isNotSelected = computed(() => isUndefinedOrNull(props.selected))

</script>

<style scoped>

</style>
