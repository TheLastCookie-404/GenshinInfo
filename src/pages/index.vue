<template>
  <div>
    <div>{{ genshinData }}</div>
  </div>
</template>

<script setup lang="ts">
  onMounted(() => {
    // console.log(getApiData());;
  });

  const { data: genshinData } = await 
  useFetch("https://gsi.fly.dev/characters/search?vision=Hydro&weapon=Catalyst");
</script> 
