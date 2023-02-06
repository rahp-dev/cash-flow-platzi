<template>
  <button
    class="text-white text-xl font-normal bg-cyan-500 border-0 w-full py-4 px-14 rounded-3xl box-border drop-shadow-md"
    @click="showModal = true"
  >
    Agregar Movimiento
  </button>

  <teleport to="#app">
    <Modal v-show="showModal" @close="showModal = false">
      <form @submit.prevent="submit" class="text-xl w-full">
        <div class="flex flex-col justify-between py-4 px-6">
          <label class="mb-2 font-semibold text-slate-900">Título</label>
          <input
            type="text"
            class="text-xl border-2 border-sky-500 rounded-lg p-2 drop-shadow-lg"
            v-model="title"
          />
        </div>

        <div class="flex flex-col justify-between py-4 px-6">
          <label class="mb-2 font-semibold text-slate-900">Monto</label>
          <input
            type="number"
            class="text-right text-xl border-2 border-sky-500 rounded-lg p-2 drop-shadow-lg"
            v-model="amount"
          />
        </div>

        <div class="flex flex-col justify-between py-4 px-6">
          <label class="mb-2 font-semibold text-slate-900">Descripción</label>
          <textarea
            rows="4"
            class="text-xl border-2 border-sky-500 rounded-lg p-2 drop-shadow-lg"
            v-model="description"
          />
        </div>

        <div class="flex flex-col justify-between px-6 pt-4">
          <label class="flex items-center mt-2 font-semibold text-slate-900">
            <input
              type="radio"
              v-model="movementType"
              value="Ingreso"
              class="appearance-none w-5 h-5 border-2 border-sky-500 rounded-3xl checked:bg-sky-500"
            />
            <span class="ml-2">Ingreso</span>
          </label>
        </div>

        <div class="flex flex-col justify-between px-6">
          <label class="flex items-center mt-2 font-semibold text-slate-900">
            <input
              type="radio"
              v-model="movementType"
              value="Gasto"
              class="appearance-none w-5 h-5 border-2 border-sky-500 rounded-3xl checked:bg-sky-500"
            />
            <span class="ml-2">Gasto</span>
          </label>
        </div>

        <div class="flex items-center justify-center mt-8">
          <button
            class="text-white text-xl font-normal bg-cyan-500 border-0 py-4 px-14 rounded-3xl box-border drop-shadow-md"
          >
            Agregar movimiento
          </button>
        </div>
      </form>
    </Modal>
  </teleport>
</template>

<script setup>
import { ref, defineEmits } from "vue";
import Modal from "./Modal.vue";

const showModal = ref(false);
const title = ref("");
const amount = ref(0);
const description = ref("");
const movementType = ref("Ingreso");

const submit = () => {
  showModal.value = !showModal.value;

  emit("create", {
    title: title.value,
    description: description.value,
    amount: movementType.value === "Ingreso" ? amount.value : -amount.value,
    time: new Date(),
    id: new Date().getDate(),
  });

  title.value = "";
  description.value = "";
  amount.value = 0;
  movementType.value = "Ingreso";
};

const emit = defineEmits(["create"]);
</script>

<style scoped></style>
