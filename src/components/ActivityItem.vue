<template>
  <li class="flex flex-col gap-2 p-4">
    <div class="flex items-center gap-2">
      <BaseButton :type="BUTTON_TYPE_DANGER">
        <TrashIcon class="h-8"/>
      </BaseButton>
      <span class="truncate text-xl">{{ activity }}</span>
    </div>
    <div class="flex gap-2">
      <BaseSelect
        class="grow font-mono"
        placeholder="hh:mm"
        :options="PERIOD_SELECT_OPTIONS"
        :selected="secondToComplete"
        @select="secondToComplete = $event"
      />
    </div>
  </li>
</template>

<script setup>
import BaseButton from './BaseButton.vue'
import { TrashIcon } from '@heroicons/vue/24/outline'
import BaseSelect from './BaseSelect.vue'
import { ref } from 'vue'
import { PERIOD_SELECT_OPTIONS, BUTTON_TYPE_DANGER } from '../constants'
import { isActivityValid } from '../validators'

defineProps({
  activity: {
    type: String,
    required: true,
    validator: isActivityValid
  }
})


const secondToComplete = ref(null)
</script>

<style scoped>

</style>
