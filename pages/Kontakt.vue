<template>
    <div
        class="overflow-x-hidden entirePage h-[calc(100vh-80px)] min-h-[700px] w-screen bg-[#D9D9D9] dark:bg-[#1B1B1B] flex items-center justify-center"
    >
        <Kontakt id="kontakt" />
    </div>
</template>

<script setup lang="ts">
import gsap from 'gsap';
import { onMounted, ref } from 'vue';
const activePage = ref('Kontakt');
const activePageUpdate = (value: string) => {
    activePage.value = value;

    if (value === 'Start') {
        fadeOutRef.value();
    }
};

const fadeOutRef = ref(() => {})

onMounted(() => {

    gsap.fromTo('#kontakt', { x: '100%' }, { x: '0%', duration: 0.5 });

    const fadeOut = () => {
        gsap.to('#kontakt', { 
            x: '100%',
            duration: 0.5,
            onComplete: () => {
                navigateTo('/');
            },
        });
    }

    fadeOutRef.value = fadeOut;
})
</script>

<style scoped></style>
