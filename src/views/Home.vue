<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div class="counter" :style="{ color: $store.state.colorCode }">
      {{ $store.state.counter }}
    </div>
    <div class="counter-squered">
      {{ $store.state.counter }}
      <sup>2</sup> = {{ $store.getters.counterSquere }}
    </div>
    <div class="buttons">
      <button @click="$store.dispatch('decreaseCounter')">-</button>
      <button @click="$store.dispatch('increaseCounter')">+</button>
    </div>
    <div>
      <input v-model="colorCode" placeholder="Enter color code" type="text" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  computed: {
    colorCode: {
      get() {
        return this.$store.state.colorCode;
      },
      set(newValue) {
        this.$store.dispatch("setColorCode", newValue);
      },
    },
  },
};
</script>

<style>
div {
  margin-top: 10px;
}

.counter {
  font-size: 80px;
}

.buttons button {
  font-size: 40px;
  width: 100px;
  margin: 0 10px;
  cursor: pointer;
}
</style>
