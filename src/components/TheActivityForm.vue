<script setup>
import BaseButton from './BaseButton.vue'
import { isActivityValid } from '../validators'
import { PlusIcon } from '@heroicons/vue/24/outline'

const emit = defineEmits({
  submit: isActivityValid,
})

let activity = 'New Task'

function submit() {
  emit('submit', activity)
}
</script>

<template>
  <form @submit.prevent="submit" class="sticky bottom-[57px] flex gap-2 border-t bg-white p-4">
    <input
      :value="activity"
      type="text"
      @input="activity = $event.target.value"
      class="w-full rounded border px-4 text-xl"
      placeholder="Activity name"
    />
    <BaseButton>
      <PlusIcon class="h-8" />
    </BaseButton>
  </form>
</template>
