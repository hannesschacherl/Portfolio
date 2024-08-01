<template>
    <div class="w-full h-20 flex justify-center items-center gap-2">
        <div
            class="bg-white dark:bg-[#3D3D3D] p-2 rounded-xl flex gap-2 text-md font-bold shadow-md"
        >
            <div
                @click="startClicked()"
                class="p-2 text-black dark:text-white hover:cursor-pointer select-none"
                :class="activePage === 'Start' ? 'bg-[#D9D9D9] dark:bg-[#5D5D5D] rounded-lg' : ''"
            >
                Start
            </div>
            <div
                @click="kontaktClicked()"
                class="p-2 rounded-lg text-black dark:text-white hover:cursor-pointer select-none"
                :class="activePage === 'Kontakt' ? 'bg-[#D9D9D9] dark:bg-[#5D5D5D] rounded-lg' : ''"
            >
                Kontakt
            </div>
        </div>
        <div
            class="bg-white dark:bg-[#3D3D3D] p-2 rounded-xl flex gap-2 text-md font-bold shadow-md"
        >
            <div
                class="p-2 text-black dark:text-white cursor-pointer hover:bg-[#D9D9D9] dark:hover:bg-[#5D5D5D] rounded-lg"
                @click="changeColorSchemeRef"
            >
                <svg
                    v-if="darkMode"
                    class="w-6 h-6"
                    fill="currentColor"
                    viewBox="0 0 20 20"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                        d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"
                    ></path>
                </svg>
                <svg
                    v-else
                    class="w-6 h-6"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                        d="M12 3V4M12 20V21M4 12H3M6.31412 6.31412L5.5 5.5M17.6859 6.31412L18.5 5.5M6.31412 17.69L5.5 18.5001M17.6859 17.69L18.5 18.5001M21 12H20M16 12C16 14.2091 14.2091 16 12 16C9.79086 16 8 14.2091 8 12C8 9.79086 9.79086 8 12 8C14.2091 8 16 9.79086 16 12Z"
                        stroke="currentColor"
                        stroke-width="2"
                        stroke-linecap="round"
                        stroke-linejoin="round"
                    />
                </svg>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const props = defineProps<{
    activePage: string;
}>();

const emit = defineEmits<{
    (e: 'update:activePage', value: string): void;
}>();

const startClicked = () => {
    emit('update:activePage', 'Start');
};

const kontaktClicked = () => {
    emit('update:activePage', 'Kontakt');
};



const darkMode = ref(true);
const changeColorSchemeRef = ref(() => {});
onMounted(() => {
    if (localStorage.getItem('color-theme') === 'light') {
        darkMode.value = false;
    }
    const changeColorScheme = () => {
        if (darkMode.value) {
            document.documentElement.classList.remove('dark');
            localStorage.setItem('color-theme', 'light');
            darkMode.value = false;
        } else {
            document.documentElement.classList.add('dark');
            localStorage.setItem('color-theme', 'dark');
            darkMode.value = true;
        }
    };
    changeColorSchemeRef.value = changeColorScheme;
});
</script>

<style scoped></style>
