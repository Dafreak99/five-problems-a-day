<template>
  <nav class="nav">
    <div class="container nav__content">
      <h3 class="nav__logo">Logo</h3>
    </div>
  </nav>
</template>

<script>
export default {
  name: "navbar",
};
</script>

<style lang="scss">
.nav {
  @apply h-14 flex shadow-xl;
  background: #1e2023;

  &__content {
    @apply flex items-center justify-between text-white text-2xl;
  }
}
</style>
