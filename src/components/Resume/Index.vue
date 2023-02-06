<template>
  <main class="flex flex-col justify-center items-center w-full">
    <p class="m-0 text-center text-xl font-medium text-stone-700">
      {{ selectedDate }}
    </p>

    <h1 class="m-0 text-center mt-3.5 text-emerald-500 text-2xl font-semibold">
      {{ amountCurrency }}
    </h1>

    <div class="flex justify-center items-center w-full py-12 px-6">
      <slot name="graphic"></slot>
    </div>

    <div class="">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script>
const currencyFormatter = new Intl.NumberFormat("en-US", {
  style: "currency",
  currency: "USD",
});

export default {
  props: {
    label: {
      type: String,
    },
    amount: {
      type: Number,
      default: null,
    },
    totalAmount: {
      type: Number,
    },
    dateLabel: {
      type: String,
      default: null,
    },
  },
  computed: {
    amountVisual() {
      return this.amount !== null ? this.amount : this.totalAmount;
    },
    selectedDate() {
      return this.dateLabel !== null ? this.label : this.dateLabel;
    },
    amountCurrency() {
      return currencyFormatter.format(this.amountVisual);
    },
  },
};
</script>
