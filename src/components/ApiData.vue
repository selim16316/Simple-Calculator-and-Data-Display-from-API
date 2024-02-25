<script>
import { ref, onMounted } from 'vue';

export default {
  name: 'QuoteComponent',
  setup() {
    const quoteData = ref({});
    const isLoading = ref(true);

    const fetchData = async () => {
      try {
        const response = await fetch('https://animechan.xyz/api/random');
        const data = await response.json();
        quoteData.value = data;
        isLoading.value = false;
      } catch (error) {
        console.error('Error fetching data:', error);
        isLoading.value = false;
      }
    };

    onMounted(() => {
      fetchData();
    });

    return {
      quoteData,
      isLoading
    };
  }
};
</script>


<template>
<section class="max-w-[700px] mt-5 mb-20 mx-5 md:mx-auto shadow-lg shadow-slate-100 px-5 py-10 border rounded">
    <h2 class="text-center text-2xl font-bold mb-3">Display data from an API</h2>
  
    <div class="p-4">
    <div v-if="isLoading" class="text-center">
      <p>Loading...</p>
    </div>
    <div v-else>
      <div class="border rounded p-4">
        <p class="mb-2"><strong>ID:</strong> {{ quoteData.id }}</p>
        <p class="mb-2"><strong>Quote:</strong> {{ quoteData.quote }}</p>
        <p class="mb-2"><strong>Anime:</strong> {{ quoteData.anime }}</p>
        <p><strong>Character:</strong> {{ quoteData.character }}</p>
      </div>
    </div>
  </div>
</section>
</template>


<style scoped>

</style>