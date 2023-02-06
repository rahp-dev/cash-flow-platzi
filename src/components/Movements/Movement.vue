<template>
  <div
    class="flex justify-between items-center w-full p-4 bg-sky-200 rounded-lg box-border"
  >
    <div class="w-full">
      <h4 class="m-0 p-0 mb-2 text-lg font-medium">{{ title }}</h4>
      <p class="m-0 p-0 text-md">{{ description }}</p>
    </div>

    <div class="flex flex-col justify-between items-end">
      <img
        src="@/assets/trash-icon.svg"
        class="mb-4"
        alt="trash"
        @click="remove"
      />
      <p
        class="m-0 p-0 font-medium"
        :class="{ red: isNegative, green: !isNegative }"
      >
        {{ amountCurrency }}
      </p>
    </div>
  </div>
</template>

<script setup>
import { toRefs, defineProps, defineEmits, computed } from "vue";

const currencyFormatter = new Intl.NumberFormat("en-US", {
  style: "currency",
  currency: "USD",
});

const props = defineProps({
  id: {
    type: Number,
  },
  title: {
    type: String,
  },
  description: {
    type: String,
  },
  amount: {
    type: Number,
  },
});

const { id, title, description, amount } = toRefs(props);

const amountCurrency = computed(() => currencyFormatter.format(amount.value));

const isNegative = computed(() => amount.value < 0);

const emit = defineEmits(["remove"]);

const remove = () => {
  emit("remove", id.value);
};
</script>

<style scoped>
.red {
  color: red;
}
.green {
  color: green;
}
</style>
