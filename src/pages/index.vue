<template>
  <div>Lol</div>
</template>

<script setup lang="ts">
  onMounted(() => {
    console.log(getApiData());
  });

  async function getApiData() {
    const res = await $fetch('https://gsi.fly.dev/', {
      method: 'GET',
    });
    return res;
  };
</script>