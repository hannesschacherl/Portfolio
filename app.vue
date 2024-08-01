<template>
  <div class="overflow-x-hidden overflow-y-auto">
    <NuxtPage />
  </div>
</template>

<script setup lang="ts">
onMounted(() => {
    if (localStorage.getItem('color-theme') === 'light') {
        document.documentElement.classList.remove('dark');
    } else {
        document.documentElement.classList.add('dark');
    }
});
</script>

<style>

</style>