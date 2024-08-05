<template>
    <div
        class="container mx-auto lg:px-32 h-[700px] pb-6 flex items-center justify-center"
    >
        <div
            class="w-full h-full max-w-[800px] gap-4 grid grid-rows-7 grid-cols-2 md:grid md:grid-rows-6 md:grid-cols-3"
        >
            <div
                class="container1 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] row-span-3 md:row-span-3"
            ></div>
            <div
                class="container2 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] hidden md:row-span-2 md:col-span-2 md:block"
            ></div>
            <div
                class="container3 bg-white shadow-md dark:bg-[#3D3D3D] rounded-2xl row-span-2 md:row-span-2"
            ></div>
            <div
                class="container4 bg-white shadow-md dark:bg-[#3D3D3D] rounded-2xl row-start-4 row-span-4 col-span-2 md:row-span-4 md:row-start-3 md:col-start-3 md:col-span-1"
            ></div>
            <div
                class="container5 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] md:col-start-1 md:row-start-4"
            ></div>
            <div
                class="container6 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] hidden md:block md:row-span-2 md:col-span-2"
            ></div>
        </div>
    </div>
</template>

<script setup lang="ts">
import gsap from 'gsap';

onMounted(() => {
  const container = document.querySelector('.container');

  const mm = gsap.matchMedia();

  mm.add('(min-width: 768px)', () => {
    const tl = gsap.timeline({
      onStart: () => {
        if(container)container.classList.add('overflow-hidden')
      },
      onComplete: () => {
        if(container)container.classList.remove('overflow-hidden')
      },
    });

    tl.add(
      gsap.from('.container3', {
        duration: 0.2,
        ease: "expoScale(0.5,7,none)",
      })
    );
    tl.add(
      gsap.from('.container1', {
        duration: 0.25,
        y: -100,
        opacity: 0,
        ease: 'ease-in',
      })
    );
    tl.add(
      gsap.from('.container2', {
        duration: 0.25,
        x: 100,
        opacity: 0,
        ease: 'ease-in',
      })
    );
    tl.add(
      gsap.from('.container4', {
        duration: 0.25,
        y: 100,
        opacity: 0,
        ease: 'ease-in',
      })
    );
    tl.add(
      gsap.from('.container6', {
        duration: 0.25,
        x: -100,
        opacity: 0,
        ease: 'ease-in',
      })
    );
    tl.add(
      gsap.from('.container5', {
        duration: 0.25,
        x: -100,
        opacity: 0,
        ease: 'ease-in',
      })
    );
  });
});
</script>

<style scoped></style>
