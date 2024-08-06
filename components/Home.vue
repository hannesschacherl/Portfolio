<template>
    <div
        class="container mx-auto p-2 lg:px-32 h-[700px] pb-6 flex items-center justify-center"
    >
        <div
            class="w-full h-full max-w-[800px] gap-4 grid grid-rows-7 grid-cols-2 md:grid md:grid-rows-6 md:grid-cols-3"
        >
            <div
                class="container1 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] row-span-3 md:row-span-3"
            >
                <img
                    src="../public/Einstein2.png"
                    alt="Einstein"
                    class="w-full h-full rounded-2xl object-cover"
                />
            </div>
            <div
                class="container2 p-4 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] hidden md:row-span-2 md:col-span-2 md:block"
            >
                <div class="text-4xl text-black dark:text-white font-bold">
                    Über mich
                </div>
            </div>
            <a
                class="container3 select-none cursor-pointer bg-white shadow-md dark:bg-[#3D3D3D] rounded-2xl row-span-2 md:row-span-2"
                href="https://github.com/hannesschacherl"
                target="_blank"
            >
                <div
                    class="w-full h-full p-2 flex flex-col gap-4 items-center justify-center"
                >
                    <img
                        src="../public/github.png"
                        alt="github"
                        class="rounded-full w-14 h-14 md:w-20 md:h-20"
                    />
                    <div
                        class="text-[#00DEDE] text-center text-2xl sm:text-3xl font-bold"
                    >
                        Hannes Schacherl
                    </div>
                </div>
            </a>
            <div
                class="container4 bg-white shadow-md dark:bg-[#3D3D3D] rounded-2xl row-start-4 row-span-4 col-span-2 md:row-span-4 md:row-start-3 md:col-start-3 md:col-span-1 XsPictureStyle"
            >
                <div class="w-full h-full hidden dark:block">
                    <img
                        src="../public/Bildung.svg"
                        alt="Bildung"
                        class="w-full h-full p-2 hidden md:block"
                    />
                    <img
                        src="../public/BildungswegSm.svg"
                        alt="Bildung"
                        class="bildungswegMd w-full h-full p-2"
                    />
                    <img
                        src="../public/BildungXs.svg"
                        alt="Bildung"
                        class="bildungswegXs h-full p-4 md:hidden"
                    />
                </div>

                <div class="w-full h-full dark:hidden">
                    <img
                        src="../public/LightBildung.svg"
                        alt="Bildung"
                        class="w-full h-full p-2 hidden md:block"
                    />
                    <img
                        src="../public/LightBildungSm.svg"
                        alt="Bildung"
                        class="bildungswegMd w-full h-full p-2"
                    />
                    <img
                        src="../public/LightBildungXs.svg"
                        alt="Bildung"
                        class="bildungswegXs h-full p-4 md:hidden"
                    />
                </div>
            </div>
            <a
                class="container5 gap-2 select-none text-center relative font-bold flex items-center justify-center text-2xl sm:text-4xl w-full h-full rounded-2xl shadow-md bg-[#00DEDE] md:col-start-1 md:row-start-4"
                href="https://maps.app.goo.gl/z4jSG5gHPqTyjc3KA"
                target="_blank"
            >
                <svg
                    class=""
                    version="1.0"
                    id="Layer_1"
                    xmlns="http://www.w3.org/2000/svg"
                    xmlns:xlink="http://www.w3.org/1999/xlink"
                    width="46px"
                    viewBox="0 0 64 64"
                    enable-background="new 0 0 64 64"
                    xml:space="preserve"
                >
                    <path
                        fill="#231F20"
                        d="M32,0C18.746,0,8,10.746,8,24c0,5.219,1.711,10.008,4.555,13.93c0.051,0.094,0.059,0.199,0.117,0.289l16,24
	C29.414,63.332,30.664,64,32,64s2.586-0.668,3.328-1.781l16-24c0.059-0.09,0.066-0.195,0.117-0.289C54.289,34.008,56,29.219,56,24
	C56,10.746,45.254,0,32,0z M32,32c-4.418,0-8-3.582-8-8s3.582-8,8-8s8,3.582,8,8S36.418,32,32,32z"
                    />
                </svg>
                Fürth
            </a>
            <div
                class="container6 p-4 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] hidden md:block md:row-span-2 md:col-span-2"
            >
                <div class="text-4xl text-black dark:text-white font-bold">
                    Verwendete Technologien
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import gsap from 'gsap';

onMounted(() => {
    const container = document.querySelector('.fullpage');

    const mm = gsap.matchMedia();

    mm.add('(min-width: 768px)', () => {
        const tl = gsap.timeline({
            onStart: () => {
                if (container) container.classList.add('overflow-hidden');
            },
            onComplete: () => {
                if (container) container.classList.remove('overflow-hidden');
            },
        });

        tl.add(
            gsap.from('.container3', {
                duration: 0.2,
                ease: 'expoScale(0.5,7,none)',
            }),
        );
        tl.add(
            gsap.from('.container1', {
                duration: 0.25,
                y: -100,
                opacity: 0,
                ease: 'ease-in',
            }),
        );
        tl.add(
            gsap.from('.container2', {
                duration: 0.25,
                x: 100,
                opacity: 0,
                ease: 'ease-in',
            }),
        );
        tl.add(
            gsap.from('.container4', {
                duration: 0.25,
                y: 100,
                opacity: 0,
                ease: 'ease-in',
            }),
        );
        tl.add(
            gsap.from('.container6', {
                duration: 0.25,
                x: -100,
                opacity: 0,
                ease: 'ease-in',
            }),
        );
        tl.add(
            gsap.from('.container5', {
                duration: 0.25,
                x: -100,
                opacity: 0,
                ease: 'ease-in',
            }),
        );
    });

    mm.add('(min-width: 350px) and (max-width: 767px)', () => {
        const tl = gsap.timeline({
            onStart: () => {
                if (container) container.classList.add('overflow-hidden');
            },
            onComplete: () => {
                if (container) container.classList.remove('overflow-hidden');
            },
        });

        tl.add(
            gsap.from('.container1', {
                duration: 0.3,
                x: -100,
                opacity: 0,
                ease: 'ease-in',
            }),
        )
            .add(
                gsap.from('.container3', {
                    duration: 0.3,
                    y: -100,
                    opacity: 0,
                    ease: 'ease-in',
                }),
            )
            .add(
                gsap.from('.container5', {
                    duration: 0.3,
                    x: 100,
                    opacity: 0,
                    ease: 'ease-in',
                }),
            )
            .add(
                gsap.from('.container4', {
                    duration: 0.3,
                    y: 100,
                    opacity: 0,
                    ease: 'ease-in',
                }),
            );
    });
});
</script>

<style scoped>
.bildungswegMd {
    display: none;
}

@media (min-width: 450px) and (max-width: 767px) {
    .bildungswegMd {
        display: block;
    }
}

.bildungswegXs {
    display: none;
}

@media (max-width: 449px) {
    .bildungswegXs {
        display: block;
    }
}
</style>
