<template>
  <div class="flex items-center justify-center bg-indigo-600 w-screen h-screen">
    <div class="bg-white shadow-lg py-12 px-6 md:px-24 rounded-lg inner">
      <v-table />
    </div>
  </div>
</template>

<script>
import VTable from "@/components/VTable";

export default {
  name: "IndexPage",
  components: {
    VTable,
  },
};
</script>

<style scoped>
.inner {
  width: 1000px;
}

@media screen and (max-width: 1200px) {
  .inner {
    width: 768px;
  }
}

@media screen and (max-width: 768px) {
  .inner {
    width: 90vw;
  }
}

html {
  -webkit-user-select: none; /* Safari */
  -ms-user-select: none; /* IE 10 and IE 11 */
  user-select: none; /* Standard syntax */
}
</style>
