<template>
    <div class="flex flex-col items-center justify-center min-h-screen bg-gray-100 p-4">
        <input v-model="numbers" class="border p-3 rounded-md w-full max-w-lg"
            placeholder="Wpisz liczby po przecinku" />
        <button @click="findOddValue"
            class="bg-blue-600 text-white px-6 py-3 mt-4 rounded-md hover:bg-blue-800 transition duration-300">
            Wyszukaj
        </button>

        <p v-if="errorMessage" class="text-red-600 mt-4">{{ errorMessage }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            numbers: '',
            errorMessage: null,
        };
    },
    methods: {
        findOddValue() {
            const numArray = this.numbers.split(',').map(value => value.trim());
            const isValid = numArray.every(val => !isNaN(val) && val !== '');

            if (!isValid) {
                this.errorMessage = 'Wpisano niepoprawne dane. Proszę wpisać tylko liczby oddzielone przecinkami.';
            } else {
                this.errorMessage = null;
                const numericArray = numArray.map(Number);
                this.$emit('search', numericArray);
            }
        },
    },
};
</script>