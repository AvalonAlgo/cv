<script setup lang="ts">
  const isOpen = ref(false);
  const route = useRoute();
</script>

<template>
  <div
    class="flex flex-row justify-between p-8 items-center rounded-lg bg-gray-900"
  >
    <h1 class="text-3xl subpixel-antialiased font-semibold">Deniz Keskin</h1>
    <UButton
      @click="isOpen = true"
      class="text-2xl subpixel-antialiased"
      label="Navigate"
      variant="soft"
    />
  </div>

  <UModal v-model="isOpen">
    <div class="p-4 flex flex-col space-y-2">
      <UButton label="Home" to="/" variant="soft" color="emerald" block />
    </div>
  </UModal>
</template>
