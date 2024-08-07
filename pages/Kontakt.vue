<template>
    <div
        class="overflow-x-hidden entirePage h-screen min-h-[800px] w-screen bg-[#D9D9D9] dark:bg-[#1B1B1B] flex flex-col gap-6"
    >
        <NavBar
            class=""
            :activePage="activePage"
            @update:activePage="activePageUpdate"
        />
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
