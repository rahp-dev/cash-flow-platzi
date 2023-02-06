<template>
  <div class="max-h-full py-0 px-2 mb-3.5">
    <h2
      class="text-2xl font-bold pt-2 pr-4 pb-6 pl-4 text-sky-500 drop-shadow-lg"
    >
      Historial
    </h2>
    <hr class="mb-6" />
    <div class="flex flex-col gap-2 overflow-y-scroll" style="max-height: 68vh">
      <Movement
        v-for="{ id, title, description, amount } in movements"
        :key="id"
        :id="id"
        :title="title"
        :description="description"
        :amount="amount"
        @remove="remove"
      />
    </div>
  </div>
</template>

<script setup>
import { toRefs, defineProps, defineEmits } from "vue";
import Movement from "./Movement.vue";

const props = defineProps({
  movements: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["remove"]);

const { movements } = toRefs(props);

const remove = (id) => {
  emit("remove", id);
};
</script>
