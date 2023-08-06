<template>
  <li class="relative flex flex-col gap-2 border border-gray-200 py-10 px-4">
    <TimelineHour :hour="timelineItem.hour"/>
    <BaseSelect
      :options="options"
      placeholder="Rest"
      :selected="selectedActivityId"
      @select="selectedActivityId = $event"
    />
  </li>
</template>

<script setup>
import { ref, defineProps } from 'vue'
import { isTimelineItemValid } from '../validators'
import BaseSelect from './BaseSelect.vue'
import TimelineHour from './TimelineHour.vue'

defineProps({
  timelineItem: {
    type: Object,
    required: true,
    validator: isTimelineItemValid
  }
})

const selectedActivityId = ref(1)

const options = [
  {
    value: 1,
    label: 'Coding'
  },
  {
    value: 2,
    label: 'Reading'
  },
  {
    value: 3,
    label: 'Training'
  },
]

</script>

<style scoped>

</style>
