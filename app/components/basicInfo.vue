<script setup lang="ts">
import type { FormError, FormSubmitEvent } from '@nuxt/ui'

const state = reactive({
  fName: undefined,
  // password: undefined
})

const validate = (state: any): FormError[] => {
  const errors: FormError[] = []
  if (!state.email) errors.push({ name: 'fName', message: 'Required' })
  return errors
}

const toast = useToast()
async function onSubmit(event: FormSubmitEvent<typeof state>) {
  toast.add({ title: 'Save Info.', description: 'The form has been submitted.', color: 'success' })
  debugger
  validate(state)
}
</script>

<template>
  <div>
    <UCard>
      <template #header>
        Basic Information Form
      </template>
      <UForm :validate="validate" :state="state" class="space-y-4" @submit="onSubmit">
        <UFormField label="Full name" name="fName">
          <UInput v-model="state.fName" />
        </UFormField>
        <UButton type="submit" @submit="onSubmit">
          Save Info.
        </UButton>
      </UForm>
    </UCard>
  </div>
</template>

<style scoped></style>
