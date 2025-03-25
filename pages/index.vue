<template>
  <div v-auto-animate class="bg-base-100 flex h-[80vh] gap-3 p-3">
    <button
      v-for="elem in tiles"
      :key="elem"
      class="btn btn-neutral"
      @click="tiles = removeItem(elem, tiles)">
      {{ elem }}
    </button>
    <button class="btn btn-success" @click="tiles = tilesDefault">Resset</button>
    <div class="dev h-fit p-3">{{ runTimeConfig.public.LOL_ENV }}</div>
  </div>
  <!-- <div>
    <div v-for="n in 5" class="dev h-64">lol</div>
  </div> -->
</template>

<script setup lang="ts">
  const tilesDefault: string[] = ["lol", "kek", "azaza", "amogu", "ubuntus"];
  const tiles = ref<string[]>(tilesDefault);
  const runTimeConfig = useRuntimeConfig();

  useAutoAnimate({ duration: 200 });

  function removeItem(toRemove: string, arr: string[]) {
    return arr.filter((item) => item !== toRemove);
  }
</script>
