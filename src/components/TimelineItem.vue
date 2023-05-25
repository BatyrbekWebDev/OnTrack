<script setup>
import { ref } from 'vue'
import { isTimelineItemValid } from '../validators'
import BaseSelect from './BaseSelect.vue'
import TimelineHour from './TimelineHour.vue'

defineProps({
  timelineItem: {
    required: true,
    type: Object,
    validator: isTimelineItemValid
  }
})

const options = [
  { value: 1, label: 'Coding' },
  { value: 2, label: 'Reading' },
  { value: 3, label: 'Trainig' }
]

const selectedActivityId = ref(1)
</script>
<template>
  <li class="relative flex flex-col gap-2 border-t border-gray-200 px-4 py-10">
    <TimelineHour :hour="timelineItem.hour"/>
    <BaseSelect
      :selected="selectedActivityId"
      :options="options"
      placeholder="Rest"
      @select="selectedActivityId = $event"
    />
  </li>
</template>
