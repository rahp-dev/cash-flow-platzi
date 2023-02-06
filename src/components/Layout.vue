<template>
  <div
    class="flex justify-around items-center py-3.5 box-border fixed w-screen"
  >
    <slot name="header"></slot>
  </div>

  <div class="flex justify-around items-center py-3.5 box-border min-h-screen">
    <slot name="resume"></slot>
  </div>

  <div
    class="flex flex-col justify-around items-center py-3.5 box-border z-10 absolute w-screen bg-slate-100"
    style="box-shadow: 0 -8px 20px #e5e5e5; bottom: 0"
  >
    <div
      class="flex justify-center items-center p-6 w-full box-border"
      @click="showMovements = !showMovements"
    >
      <div class="w-32 h-2 bg-slate-500 rounded"></div>
    </div>
    <div class="w-full" style="height: 75vh" v-show="showMovements">
      <slot name="movements"></slot>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const showMovements = ref(false);
</script>
