<template>
  <button :class="`${typesClasses[type]} rounded bg-gray-100 p-3 disabled:cursor-not-allowed disabled:opacity-50`">
    <slot></slot>
  </button>
</template>

<script>
import { BUTTON_TYPE_DANGER, BUTTON_TYPE_NEUTRAL } from '../constants'
const typesClasses = {
  [BUTTON_TYPE_NEUTRAL]: 'bg-gray-100 enabled:hover:bg-gray-200',
  [BUTTON_TYPE_DANGER]: 'bg-red-500 enabled:hover:bg-red-600 text-white'
}
</script>

<script setup>
import { isButtonTypeValid } from '../validators'

defineProps({
  type: {
    type: String,
    default: BUTTON_TYPE_NEUTRAL,
    validator: isButtonTypeValid
  }
})
</script>

<style scoped>

</style>
