<script setup lang="ts">
import { ref, onMounted } from "vue";

const colorMode = useColorMode();
const isMounted = ref(false);

onMounted(() => {
  isMounted.value = true;
});

function toggleColorMode() {
  colorMode.preference = colorMode.preference === "dark" ? "light" : "dark";
}
</script>

<template>
  <header
    class="fixed top-0 left-0 w-screen h-12 px-4 py-2 flex items-center justify-between bg-sky-200 dark:bg-sky-800 text-sky-950 dark:text-sky-50"
  >
    <h1 class="text-2xl font-semibold">Tickets</h1>
    <button
      class="rounded-full border-2 border-cyan-950 dark:border-cyan-50 p-1 flex items-center justify-center"
      @click="toggleColorMode"
    >
      <Icon
        v-if="isMounted && colorMode.preference === 'dark'"
        name="ph:sun-fill"
        class="w-12 h-12"
      />
      <Icon v-else-if="isMounted" name="ph:moon-fill" class="w-12 h-12" />
    </button>
  </header>
</template>
