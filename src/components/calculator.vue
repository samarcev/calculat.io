<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      result: "0",
    };
  },
  methods: {},
  mounted() {
    document.querySelectorAll(".numpad button").forEach((b) => {
      b.addEventListener("click", () => {
        try {
          const action = b.textContent!.trim().toString();
          if (action === "=") {
            this.result = eval(this.result).toString();
            return;
          }
          if (action === "C") {
            this.result = "0";
            return;
          }
          if (this.result === "0") {
            this.result = action;
          } else {
            this.result += action;
          }
        } catch (e) {
          this.result = "0";
        }
      });
    });
  },
});
</script>

<template>
  <div class="w-full bg-white rounded-xl p-4 shadow-xl border shadow-gray-900">
    <div class="result">
      <input
        class="w-full h-full p-4 bg-gray-300 border-2 text-3xl rounded-t-2xl text-right"
        readonly
        placeholder="0"
        v-model="result"
      />
    </div>
    <div class="numpad grid grid-cols-4 text-2xl gap-1.5">
      <div class="col-span-3 grid grid-cols-3 gap-1.5 pt-1.5 text-white">
        <div class="col-span-3 actions grid grid-cols-3 gap-1.5">
          <button class="p-4 bg-red-600">C</button>
          <button class="p-4 bg-gray-500 text-white">/</button>
          <button class="p-4 bg-gray-500 text-white">*</button>
        </div>
        <button class="p-4 bg-gray-900">9</button>
        <button class="p-4 bg-gray-900">8</button>
        <button class="p-4 bg-gray-900">7</button>
        <button class="p-4 bg-gray-900">6</button>
        <button class="p-4 bg-gray-900">5</button>
        <button class="p-4 bg-gray-900">4</button>
        <button class="p-4 bg-gray-900">3</button>
        <button class="p-4 bg-gray-900">2</button>
        <button class="p-4 bg-gray-900">1</button>
        <button class="col-span-2 p-4 bg-gray-900 rounded-bl-2xl">0</button>
        <button class="p-4 bg-gray-900">.</button>
      </div>
      <div class="col-span-1 grid gap-1.5 pt-1.5 grid-rows-5">
        <button class="p-4 bg-gray-500 text-white">%</button>
        <button class="p-4 bg-gray-500 text-white">-</button>
        <button class="p-4 bg-gray-500 text-white">+</button>
        <button class="p-4 bg-gray-500 rounded-br-2xl text-white row-span-2">
          =
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss"></style>
