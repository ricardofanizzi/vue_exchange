<template>
  <div class="flex justify-center">
    <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100" />
    <px-assets-table v-if="!isLoading" :assets="assets" />
  </div>
</template>

<script>
import PxAssetsTable from "@/components/PxAssetsTable";
import api from "@/api";

export default {
  name: "Home",
  components: {
    PxAssetsTable,
  },
  data() {
    return {
      isLoading: false,
      assets: [],
    };
  },
  async created() {
    this.isLoading = true;

    this.assets = await api.getAssets();
    this.isLoading = false;
  },
};
</script>
