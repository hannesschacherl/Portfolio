<template>
    <div
        class="overflow-x-hidden overflow-y-clip entirePage h-[calc(100vh-80px)] min-h-[700px] w-screen bg-[#D9D9D9] dark:bg-[#1B1B1B] flex flex-col gap-6"
    >
        <Home id="home" />
    </div>
</template>

<script setup lang="ts">
import gsap from 'gsap';
const activePage = ref('Start');
const activePageUpdate = (value: string) => {
    activePage.value = value;
    if (value === 'Kontakt') {
        fadeOutRef.value();
    }
};

const fadeOutRef = ref(() => {})

onMounted(() => {
    const fadeOut = () => {
        gsap.to('#home', { 
            x: '-100%',
            duration: 0.5,
            onComplete: () => {
                navigateTo('/Kontakt');
            },
        });
    };

    fadeOutRef.value = fadeOut;
});
</script>

<style scoped></style>
