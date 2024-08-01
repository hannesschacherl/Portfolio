<template>
    <div class="h-screen w-screen bg-[#D9D9D9] dark:bg-[#1B1B1B]">
        <NavBar :activePage="activePage" @update:activePage="activePageUpdate"/>
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