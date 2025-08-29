<script setup lang="ts">
import type { StepperItem } from '@nuxt/ui'
import BasicInfo from '~/components/basicInfo.vue';
import AddressInfo from '~/components/addressInfo.vue';
import displayInfo from '~/components/displayInfo.vue';
const items: StepperItem[] = [
  {
    title: 'Basic Information',
    slot: 'basicInfo' as const
  }, 
  {
    title: 'Address Information',
    slot: 'addressInfo' as const
  }, 
  {
    title: 'Display Information',
    slot: 'displayInfo' as const
  }
]

const stepper = useTemplateRef('stepper')
</script>
<template>
    <div class="w-full">
      <UStepper ref="stepper" :items="items">
        <template #basicInfo>
          <BasicInfo />
        </template>

        <template #addressInfo>
          <AddressInfo />
        </template>
        
        <template #displayInfo>
          <displayInfo />
        </template>
      </UStepper>

      <div class="flex gap-2 justify-between mt-4">
        <UButton leading-icon="i-lucide-arrow-left" :disabled="!stepper?.hasPrev" @click="stepper?.prev()">
          Prev
        </UButton>

        <UButton trailing-icon="i-lucide-arrow-right" :disabled="!stepper?.hasNext" @click="stepper?.next()">
          Next
        </UButton>
      </div>
    </div>
</template>

<style scoped></style>
