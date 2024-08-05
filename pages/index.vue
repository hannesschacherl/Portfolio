<template>
    <div class="fullpage h-screen min-h-[800px] w-screen bg-[#D9D9D9] dark:bg-[#1B1B1B] flex flex-col gap-6">
        <NavBar :activePage="activePage" @update:activePage="activePageUpdate"/>
        <div class="flex-grow"></div>
        <Home />
        <div class="flex-grow"></div>
    </div>
</template>

<script setup lang="ts">
const activePage = ref('Start');
const activePageUpdate = (value: string) => {
    activePage.value = value;
};
</script>

<style scoped>

</style>