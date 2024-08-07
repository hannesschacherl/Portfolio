<template>
    <div
        class="w-screen h-screen flex-col text-black grid grid-cols-1 md:grid-cols-2 items-center justify-center"
    >
        <div class="w-full h-full flex items-center justify-center">
            <form
                method="POST"
                id="form"
                class="flex flex-col h-full w-5/6 items-center justify-center gap-6"
            >
                <input
                    type="hidden"
                    name="access_key"
                    value="8f29aacd-558e-4919-a348-5218d282ddf2"
                />
                <input
                    type="hidden"
                    name="subject"
                    value="New Submission from Web3Forms"
                />
                <input
                    type="checkbox"
                    name="botcheck"
                    id=""
                    style="display: none"
                />

                <div
                    class="flex items-center w-full p-4 bg-gray-200 dark:bg-[#3d3d3d] rounded-full gap-4 text-gray-400"
                >
                    <svg
                        fill="currentColor"
                        class="w-6 h-6"
                        viewBox="0 0 32 32"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M16 15.503A5.041 5.041 0 1 0 16 5.42a5.041 5.041 0 0 0 0 10.083zm0 2.215c-6.703 0-11 3.699-11 5.5v3.363h22v-3.363c0-2.178-4.068-5.5-11-5.5z"
                        />
                    </svg>
                    <input
                        class="text-black dark:text-white font-bold placeholder:font-bold placeholder:text-gray-400 outline-none w-full h-full bg-gray-200 dark:bg-[#3d3d3d]"
                        placeholder="Name"
                        type="text"
                        name="name"
                        required
                    />
                </div>

                <div
                    class="flex items-center w-full p-4 bg-gray-200 dark:bg-[#3d3d3d] rounded-full gap-4 text-gray-400"
                >
                    <svg
                        class="w-6 h-6"
                        viewBox="0 0 24 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            d="M4 7.00005L10.2 11.65C11.2667 12.45 12.7333 12.45 13.8 11.65L20 7"
                            stroke="currentColor"
                            stroke-width="2"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        />
                        <rect
                            x="3"
                            y="5"
                            width="18"
                            height="14"
                            rx="2"
                            stroke="currentColor"
                            stroke-width="2"
                            stroke-linecap="round"
                        />
                    </svg>
                    <input
                        class="bg-gray-200 dark:bg-[#3d3d3d] text-black dark:text-white font-bold placeholder:font-bold placeholder:text-gray-400 outline-none w-full"
                        placeholder="E-Mail"
                        type="email"
                        name="email"
                        required
                    />
                </div>

                <textarea
                    class="bg-gray-200 dark:bg-[#3d3d3d] resize-none font-bold placeholder:font-bold text-black dark:text-white p-4 rounded-3xl min-h-60 max-h-60 overflow-y-auto placeholder:text-gray-400 outline-none w-full"
                    placeholder="Nachricht"
                    name="message"
                    required
                ></textarea>

                <button
                    v-if="!messageSent"
                    type="submit"
                    id="submitButton"
                    class="w-full bg-[#00DEDE] text-black font-bold p-4 rounded-full"
                    @click="sending"
                >
                    Senden
                </button>
                <div
                    v-else-if="messageSent && successful"
                    class="w-full flex items-center justify-center"
                >
                    <div
                        class="w-full bg-[#00DEDE] p-2 rounded-full flex gap-4 items-center"
                    >
                        <svg
                            class="w-12 h-12"
                            viewBox="0 0 24 24"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                        >
                            <g id="SVGRepo_bgCarrier" stroke-width="0" />

                            <g
                                id="SVGRepo_tracerCarrier"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                            />

                            <g id="SVGRepo_iconCarrier">
                                <path
                                    id="check1"
                                    opacity="0.5"
                                    d="M4 12.9L7.14286 16.5L15 7.5"
                                    stroke="#000000"
                                    stroke-width="1.5"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                />
                                <path
                                    id="check2"
                                    d="M20.0002 7.5625L11.4286 16.5625L11.0002 16"
                                    stroke="#000000"
                                    stroke-width="1.5"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                />
                            </g>
                        </svg>
                        <div class="text-xl text-black select-none font-bold">
                            Vielen Dank für Ihre Nachricht!
                        </div>
                    </div>
                </div>

                <div
                    v-else-if="messageSent && !successful"
                    class="w-full flex items-center justify-center"
                >
                    <div
                        class="w-full bg-[#00DEDE] p-2 rounded-full flex gap-4 items-center"
                    >
                        <svg
                            class="w-12 h-12"
                            viewBox="0 0 800 800"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                        >
                            <path
                                d="M533.333 266.667L266.667 533.334M400 400L533.333 533.334M266.667 266.667L333.333 333.334"
                                stroke="black"
                                stroke-width="50"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                            />
                        </svg>
                        <div class="text-xl text-black select-none font-bold">
                            Fehler beim Senden der Nachricht!
                        </div>
                    </div>
                </div>
                <div class="hidden" id="result"></div>
            </form>
        </div>
    </div>
</template>

<script setup lang="ts">
const messageSent = ref(false);
const successful = ref(false);
const sending = () => {
    const btn = document.getElementById('submitButton')
    if(btn) {
        btn.innerHTML = 'Senden...'
    }
}
onMounted(() => {
    const form = document.getElementById('form') as HTMLFormElement;
    const result = document.getElementById('result') as HTMLDivElement;

    if (form && result) {
        form.addEventListener('submit', async (e: Event) => {
            e.preventDefault();
            const formData = new FormData(form);
            const object = Object.fromEntries(formData.entries());
            const json = JSON.stringify(object);
            result.innerHTML = 'Please wait...';

            try {
                const response = await fetch(
                    'https://api.web3forms.com/submit',
                    {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                            Accept: 'application/json',
                        },
                        body: json,
                    },
                );

                const jsonResponse = await response.json();

                if (response.status === 200) {
                    messageSent.value = true;
                    successful.value = true;
                } else {
                    messageSent.value = true;
                    successful.value = false;
                }
            } catch (error) {
                messageSent.value = true;
                successful.value = false;
            }
        });
    } else {
        console.error('Form or result element not found.');
    }
});
</script>

<style scoped></style>
