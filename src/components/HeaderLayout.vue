<template>
  <header class="flex justify-around items-center w-screen">
    <img
      @click="reload"
      src="@/assets/cashflow-icon.svg"
      alt="Logo"
      class="w-12"
    />
    <h1 class="text-cyan-500 text-2xl font-bold">
      <span class="text-green-500">Cash</span>
      Flow
    </h1>
    <span class="w-12"></span>
  </header>
</template>

<script>
export default {
  methods: {
    reload() {
      location.reload();
    },
  },
};
</script>
