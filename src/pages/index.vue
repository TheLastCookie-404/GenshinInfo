<template>
  <div class="p-6">
    <label class="form-control w-full max-w-xs">
    <div class="label">
      <span class="label-text">What is your character element?</span>
    </div>
    <input v-model="vision" type="text" placeholder="Type here" class="input input-bordered w-full max-w-xs">
    </label>
    <label class="form-control w-full max-w-xs">
      <div class="label">
        <span class="label-text">What is your character weapon?</span>
      </div>
      <input v-model="weapon" type="text" placeholder="Type here" class="input input-bordered w-full max-w-xs">
    </label>
    <button class="btn mt-6" @click="refreshData()">Search</button>
    <div class="w-2/3 m-auto mt-6 p-6 bg-base-300 rounded-box">
      <div class="w-fit flex mb-6 items-center">
        <button class="btn btn-sm w-fit" @click="refreshing == false && page > 1 ? page-- : page, refreshData()">prev</button>
        <div class="mx-3 flex">Page: {{ page }}</div>
        <button class="btn btn-sm w-fit" @click="refreshing == false && page < genshinData['total_pages'] ? page++ : page, refreshData()">next</button>
      </div>
      <pre v-if="!refreshing" class="h-[55vh] overflow-scroll">{{ genshinData }}</pre>
      <span v-else class="loading loading-dots loading-md"/>
    </div>
  </div>
</template>

<script setup>
  const vision = ref('');
  const weapon = ref('');
  const page = ref(1);
  const refreshing = ref(false);

  onMounted(() => {
    // console.log(getApiData());;
  });

  const { data: genshinData } = await 
  useLazyAsyncData('genshinData', () => $fetch(`https://gsi.fly.dev/characters/search?page=${page.value}&vision=${vision.value}&weapon=${weapon.value}`));

  const refreshData = async () => {
    refreshing.value = true;
    try {
      await refreshNuxtData('genshinData');
    } finally {
      refreshing.value = false;
    }
  }
</script> 
