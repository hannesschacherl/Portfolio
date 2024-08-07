<template>
    <div class="w-full h-full flex items-center">
      <div class="container mx-auto p-2 lg:px-32 h-[700px] pb-6 flex items-center justify-center">
        <div class="w-full h-full max-w-[800px] gap-4 grid grid-rows-7 grid-cols-2 md:grid md:grid-rows-6 md:grid-cols-3">
          <div class="container1 transform -translate-y-24 opacity-0 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] row-span-3 md:row-span-3">
            <img
              src="../public/Einstein2.png"
              alt="Einstein"
              class="Portrait w-full h-full rounded-2xl object-cover"
            />
          </div>
          <div class="container2 transform translate-x-24 opacity-0 p-4 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] hidden md:row-span-2 md:col-span-2 md:block">
            <div class="text-4xl text-black dark:text-white font-bold select-none">
              Über mich
            </div>
            <div class="dark:text-white w-full h-full md:text-xl">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestiae rerum sed illum officia, voluptatum cum error, repellendus placeat at beatae reprehenderit corrupti pariatur. Dolorum facere provident itaque maxime numquam laborum.
            </div>
          </div>
          <a class="container3 transform scale-50 opacity-0 select-none cursor-pointer bg-white shadow-md dark:bg-[#3D3D3D] rounded-2xl row-span-2 md:row-span-2" href="https://github.com/hannesschacherl" target="_blank">
            <div class="w-full h-full p-2 flex flex-col gap-4 items-center justify-center">
              <img src="../public/github.png" alt="github" class="rounded-full w-14 h-14 md:w-20 md:h-20" />
              <div class="text-[#00DEDE] text-center text-2xl sm:text-3xl font-bold">
                Hannes Schacherl
              </div>
            </div>
          </a>
          <div class="container4 transform translate-y-24 opacity-0 bg-white shadow-md dark:bg-[#3D3D3D] rounded-2xl row-start-4 row-span-4 col-span-2 md:row-span-4 md:row-start-3 md:col-start-3 md:col-span-1 XsPictureStyle">
            <div class="w-full h-full hidden dark:block">
              <img src="../public/Bildung.svg" alt="Bildung" class="w-full h-full p-2 hidden md:block" />
              <img src="../public/BildungswegSm.svg" alt="Bildung" class="bildungswegMd w-full h-full p-2" />
              <img src="../public/BildungXs.svg" alt="Bildung" class="bildungswegXs h-full p-4 md:hidden" />
            </div>
            <div class="w-full h-full dark:hidden">
              <img src="../public/LightBildung.svg" alt="Bildung" class="w-full h-full p-2 hidden md:block" />
              <img src="../public/LightBildungSm.svg" alt="Bildung" class="bildungswegMd w-full h-full p-2" />
              <img src="../public/LightBildungXs.svg" alt="Bildung" class="bildungswegXs h-full p-4 md:hidden" />
            </div>
          </div>
          <a class="container5 transform -translate-x-24 opacity-0 gap-2 select-none text-center relative font-bold flex items-center justify-center text-2xl sm:text-4xl w-full h-full rounded-2xl shadow-md bg-[#00DEDE] md:col-start-1 md:row-start-4" href="https://maps.app.goo.gl/z4jSG5gHPqTyjc3KA" target="_blank">
            <svg class="" version="1.0" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="46px" viewBox="0 0 64 64" enable-background="new 0 0 64 64" xml:space="preserve">
              <path fill="#231F20" d="M32,0C18.746,0,8,10.746,8,24c0,5.219,1.711,10.008,4.555,13.93c0.051,0.094,0.059,0.199,0.117,0.289l16,24 C29.414,63.332,30.664,64,32,64s2.586-0.668,3.328-1.781l16-24c0.059-0.09,0.066-0.195,0.117-0.289C54.289,34.008,56,29.219,56,24 C56,10.746,45.254,0,32,0z M32,32c-4.418,0-8-3.582-8-8s3.582-8,8-8s8,3.582,8,8S36.418,32,32,32z" />
            </svg>
            Fürth
          </a>
          <div class="container6 transform -translate-x-24 opacity-0 p-4 rounded-2xl bg-white shadow-md dark:bg-[#3D3D3D] hidden md:block md:row-span-2 md:col-span-2 h-full">
            <div class="text-4xl text-black dark:text-white font-bold select-none">
              Verwendete Technologien
            </div>
            <div class="grid grid-cols-5 items-center justify-center h-[calc(100%-40px)] w-full">
              <div v-for="technology in technologies" :key="technology.name" class="flex items-center justify-center technology opacity-0">
                <a :href="technology.url" target="_blank" rel="noopener noreferrer">
                  <img :src="`/tech/${technology.icon}`" :alt="technology.name" class="w-12 h-12 md:w-12 md:h-12 cursor-pointer" />
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import gsap from 'gsap';
  import { onMounted, ref, onBeforeUnmount } from 'vue';
  
  const technologies = ref([
    { name: 'Nuxt', icon: 'nuxt.svg', url: 'https://nuxtjs.org/' },
    { name: 'JavaScript', icon: 'javascript.svg', url: 'https://www.javascript.com/' },
    { name: 'Python', icon: 'python.svg', url: 'https://www.python.org/' },
    { name: 'Git', icon: 'git.svg', url: 'https://git-scm.com/' },
    { name: 'GitHub', icon: 'github.svg', url: 'https://github.com/' },
    { name: 'Vue', icon: 'vue.svg', url: 'https://vuejs.org/' },
    { name: 'TypeScript', icon: 'typescript.svg', url: 'https://www.typescriptlang.org/' },
    { name: 'Java', icon: 'java.svg', url: 'https://www.java.com/' },
    { name: 'Docker', icon: 'docker.svg', url: 'https://www.docker.com/' },
    { name: 'GitLab', icon: 'gitlab.svg', url: 'https://gitlab.com/' },
  ]);
  
  const resetElementsState = () => {
    gsap.set('.container1', { y: -96, opacity: 0 });
    gsap.set('.container2', { x: 96, opacity: 0 });
    gsap.set('.container3', { scale: 0.5, opacity: 0 });
    gsap.set('.container4', { y: 96, opacity: 0 });
    gsap.set('.container5', { x: -96, opacity: 0 });
    gsap.set('.container6', { x: -96, opacity: 0 });
    gsap.set('.technology', { opacity: 0, x: -16 });
  };
  
  const startAnimations = () => {
    const container = document.querySelector('.entirePage');
    const mm = gsap.matchMedia();
  
    mm.add('(min-width: 768px)', () => {
      const tl = gsap.timeline({
        onStart: () => {
          container?.classList.add('overflow-hidden');
        },
        onComplete: () => {
          container?.classList.remove('overflow-hidden');
        },
      });
  
      tl.to('.container3', {
        duration: 0.5,
        scale: 1,
        opacity: 1,
        ease: 'expoScale(0.5, 7, none)',
      })
        .to('.container1', {
          duration: 0.3,
          y: 0,
          opacity: 1,
          ease: 'ease-in',
        })
        .to('.container2', {
          duration: 0.3,
          x: 0,
          opacity: 1,
          ease: 'ease-in',
        })
        .to(['.container4', '.container4 > *'], {
          duration: 0.3,
          y: 0,
          opacity: 1,
          ease: 'ease-in',
        })
        .to('.container6', {
          duration: 0.3,
          x: 0,
          opacity: 1,
          ease: 'ease-in',
        })
        .to('.container5', {
          duration: 0.3,
          x: 0,
          opacity: 1,
          ease: 'ease-in',
        })
        .add(
          gsap.to('.technology', {
            duration: 0.3,
            x: 0,
            opacity: 1,
            ease: 'ease-in',
            stagger: 0.1,
          }),
          '-=0.15'
        );
    });
  
    mm.add('(min-width: 340px) and (max-width: 767px)', () => {
      const tl = gsap.timeline({
        onStart: () => {
          container?.classList.add('overflow-hidden');
        },
        onComplete: () => {
          container?.classList.remove('overflow-hidden');
        },
      });
  
      tl.fromTo(
        '.container1',
        {
          y: -50,
          opacity: 0,
        },
        {
          duration: 0.3,
          y: 0,
          opacity: 1,
          ease: 'ease-in',
        }
      )
        .fromTo(
          '.container3',
          {
            scale: 0.5,
            opacity: 0,
          },
          {
            duration: 0.5,
            scale: 1,
            opacity: 1,
            ease: 'expoScale(0.5, 7, none)',
          }
        )
        .fromTo(
          '.container5',
          {
            x: 50,
            opacity: 0,
          },
          {
            duration: 0.3,
            x: 0,
            opacity: 1,
            ease: 'ease-in',
          }
        )
        .to('.container4', {
          duration: 0.3,
          y: 0,
          opacity: 1,
          ease: 'ease-in',
        });
    });
  };
  
  const initializePage = () => {
    const allImages = document.querySelectorAll('img');
    let imagesLoaded = 0;
  
    const checkAllImagesLoaded = () => {
      imagesLoaded += 1;
      if (imagesLoaded === allImages.length) {
        resetElementsState();
        observeElements();
      }
    };
  
    const observeElements = () => {
      const observer = new IntersectionObserver((entries, observer) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            startAnimations();
            observer.unobserve(entry.target);
          }
        });
      });
  
      const elements = document.querySelectorAll('.container1, .container2, .container3, .container4, .container5, .container6');
      elements.forEach((el) => observer.observe(el));
    };
  
    allImages.forEach((img) => {
      if (img.complete) {
        checkAllImagesLoaded();
      } else {
        img.addEventListener('load', checkAllImagesLoaded);
        img.addEventListener('error', checkAllImagesLoaded);
      }
    });
  
    const oldSize = ref(window.innerWidth);
    const resizeEvent = () => {
      if ((window.innerWidth < 768 && oldSize.value >= 768) || (window.innerWidth >= 768 && oldSize.value < 768)) {
        window.location.reload();
      }
      oldSize.value = window.innerWidth;
    };
  
    window.addEventListener('resize', resizeEvent);
  };
  
  onMounted(() => {
    initializePage();
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
  