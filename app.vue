<template>
  <div class="bg overflow-x-hidden overflow-y-auto bg-[#D9D9D9] dark:bg-[#1B1B1B] h-screen w-screen">
    <NavBar
            class=""
            :activePage="activePage"
            @update:activePage="activePageUpdate"
    />
    <NuxtPage/>
  </div>

</template>

<script setup lang="ts">
import { useRouter } from 'vue-router';

const router = useRouter();
import gsap from 'gsap';
const activePage = ref('Start');
if(router.currentRoute.value.path === '/Kontakt') {
    activePage.value = 'Kontakt';
}
const activePageUpdate = (value: string) => {
    activePage.value = value;
    if (value === 'Kontakt') {
        fadeOutRef.value();
    } else if (value === 'Start') {
        fadeOutRef2.value();
    }
};

const fadeOutRef = ref(() => {})
const fadeOutRef2 = ref(() => {})
const fadeInRef = ref(() => {})


onMounted(() => {
    if (localStorage.getItem('color-theme') === 'light') {
        document.documentElement.classList.remove('dark');
    } else {
        document.documentElement.classList.add('dark');
    }

    const fadeOut = () => {
        gsap.to('#home', { 
            x: '-100%',
            duration: 0.5,
            onComplete: () => {
                navigateTo('/Kontakt');
                fadeInRef.value();
            },
        });
    };

    fadeOutRef.value = fadeOut;

    const fadeOut2 = () => {
        gsap.to('#kontakt', { 
            x: '100%',
            duration: 0.5,
            onComplete: () => {
                navigateTo('/');
            },
        });
    }

    fadeOutRef2.value = fadeOut2;

    const fadeIn = () => {
      gsap.fromTo('#kontakt', { x: '100%' }, { x: '0%', duration: 0.5 });
    }

    fadeInRef.value = fadeIn;
});
</script>

<style>
/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background-color: var(--scrollbar-track-bg);
}

/* Handle */
::-webkit-scrollbar-thumb {
  background-color: var(--scrollbar-thumb-bg);
  border-radius: 2rem;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background-color: var(--scrollbar-thumb-hover-bg);
}
</style>

<style>
:root {
  --scrollbar-track-bg: #D9D9D9;
  --scrollbar-thumb-bg: #9D9D9D;
  --scrollbar-thumb-hover-bg: #CCCCCC;
}

.dark {
  --scrollbar-track-bg: #1B1B1B;
  --scrollbar-thumb-bg: #3D3D3D;
  --scrollbar-thumb-hover-bg: #555555;
}
</style>