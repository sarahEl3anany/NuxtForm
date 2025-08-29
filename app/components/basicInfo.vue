<script setup lang="ts">
import type { FormError, FormSubmitEvent } from '@nuxt/ui'

const state = reactive({
  fName: undefined,
  // password: undefined
})

const validate = (state: any): FormError[] => {
  let errors: FormError[] = []
  if(state.fName) {
    errors = removeValidation(errors, {name: 'fName'})
  } else {
    errors.push({ name: 'fName', message: 'Required' })
  }
  return errors
}
const removeValidation = (errors: FormError[], el:{name:string}): FormError[] => {
  const indexToRemove = errors.findIndex(error => error.name === el.name); // Find index of object to remove
  if (indexToRemove !== -1) {
    errors.splice(indexToRemove, 1);
  }
  return errors
}
const onSubmit = (event: FormSubmitEvent<typeof state>) => {

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
