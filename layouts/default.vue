<script setup lang="ts">
const project = 'Diététique et Interventions'
</script>

<template>
  <div class="relative slidev-layout">
    <slot />

    <!-- Footer left: project name -->
    <div class="absolute bottom-4 left-6 text-xs opacity-60 select-none">
      {{ project }} • Bloc 3
    </div>

    <!-- Footer right: page / total -->
    <div class="absolute bottom-4 right-6 text-xs opacity-60 select-none">
      {{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}
    </div>

    <!-- Progress bar -->
    <div class="absolute left-0 right-0 bottom-0 h-1 bg-gray-200/60 dark:bg-gray-700/40 rounded-t">
      <div
        class="h-full rounded-t"
        :style="{ width: ($slidev.nav.currentPage / $slidev.nav.total * 100) + '%', background: 'var(--slidev-theme-primary)' }"
      />
    </div>
  </div>
</template>

