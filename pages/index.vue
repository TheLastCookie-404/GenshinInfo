<template>
  <div v-auto-animate class="bg-base-100 flex h-[80vh] gap-3 p-3">
    <button
      v-for="elem in tiles"
      :key="elem"
      class="btn btn-neutral"
      @click="tiles = removeItem(elem, tiles)">
      {{ elem }}
    </button>
    <button class="btn btn-success" @click="tiles = tilesDefault">
      Resset
    </button>
  </div>
</template>

<script setup lang="ts">
  const tilesDefault: string[] = ["lol", "kek", "azaza", "amogu", "buntus"];
  const tiles = ref<string[]>(tilesDefault);

  useAutoAnimate({ duration: 200 });

  function removeItem(toRemove: string, arr: string[]) {
    return arr.filter((item) => item !== toRemove);
  }
</script>
