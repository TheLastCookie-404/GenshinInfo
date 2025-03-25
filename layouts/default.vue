<template>
  <div>
    <div class="sticky top-0 z-90 backdrop-blur-xs">
      <Header class="bg-base-200 opacity-70" />
      <div class="via-base-content/20 h-px bg-linear-to-r from-transparent to-transparent" />
      <Drawer />
    </div>
    <slot />
    <div class="via-base-content/20 h-px bg-linear-to-r from-transparent to-transparent" />
    <Footer class="bg-base-200" />
  </div>
</template>
