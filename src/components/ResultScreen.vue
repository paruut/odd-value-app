<template>
    <div class="flex flex-col items-center justify-center min-h-screen bg-gray-100">
        <h2 class="text-8xl text-center font-bold text-green-600 mb-4"> {{ result }}</h2>
        <button @click="goBack"
            class="bg-gray-600 text-white px-6 py-3 rounded-md hover:bg-gray-800 transition duration-300">
            Wróć
        </button>
    </div>
</template>

<script>
export default {
    props: ['result'],
    methods: {
        goBack() {
            this.$emit('goBack');
        },
    },
};
</script>