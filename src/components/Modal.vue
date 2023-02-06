<template>
  <div class="z-10 absolute left-0 right-0 top-0 bottom-0 bg-slate-100">
    <div class="flex justify-between items-center w-full py-6 px-6 box-border">
      <p class="m-0 text-2xl font-semibold text-sky-600 drop-shadow-xl">
        Nuevo Movimiento
      </p>
      <img src="@/assets/close-icon.svg" alt="close" @click="close" />
    </div>
    <div class="">
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from "vue";

const emit = defineEmits(["close"]);

const close = () => emit("close");
</script>
