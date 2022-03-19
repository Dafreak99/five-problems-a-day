<template>
  <div class="container flex gap-8 py-12">
    <div class="w-8/12">
      <v-table />
    </div>
    <div class="w-4/12">Hello world</div>
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
