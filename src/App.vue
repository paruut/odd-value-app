<template>
  <div>
    <InputScreen v-if="!showResult" @search="handleSearch" />
    <ResultScreen v-else :result="oddValue" @goBack="handleGoBack" />
  </div>
</template>

<script>
import InputScreen from './components/InputScreen.vue';
import ResultScreen from './components/ResultScreen.vue';

export default {
  components: {
    InputScreen,
    ResultScreen,
  },
  data() {
    return {
      showResult: false,
      oddValue: null,
    };
  },
  methods: {
    handleSearch(numbers) {
      const odd = numbers.filter(n => n % 2 !== 0);
      const even = numbers.filter(n => n % 2 === 0);
      this.oddValue = odd.length === 1 ? odd[0] : even[0];
      this.showResult = true;
    },
    handleGoBack() {
      this.showResult = false;
      this.oddValue = null;
    },
  },
};
</script>
