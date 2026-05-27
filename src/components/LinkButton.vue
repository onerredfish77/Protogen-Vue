<script setup lang="ts">
defineProps<{
  label: string
  url: string
  icon: string
}>()
</script>

<template>
  <v-btn
    :href="url"
    target="_blank"
    rel="noopener noreferrer"
    variant="tonal"
    size="large"
    block
  >
    <template #prepend>
      <v-icon :icon="icon" color="primary" />
    </template>
    {{ label }}
  </v-btn>
</template>
