<template>
  <section class="container">
    <search-bar :products="filteredProducts" @search="handleSearch" />
    <range-selector :products="filteredProducts" v-model="max" />
    <button @click="refresh" class="btn btn-primary">Refresh</button>
    <transition-group name="products" appear>
      <div
        v-for="item in filteredProducts"
        :key="item.id"
        id="item-list"
        class="row align-items-center"
      >
        <product :item="item"></product>
      </div>
    </transition-group>
  </section>
</template>
<script>
import Product from "@/components/Product";
import RangeSelector from "@/components/RangeSelector";
import SearchBar from "@/components/SearchBar";
export default {
  name: "HomeView",
  data: function () {
    return { max: 50, cart: [], displayCart: false, inputText: "" };
  },
  props: ["products"],
  components: { Product, RangeSelector, SearchBar },
  methods: {
    handleSearch(inputText) {
      console.log("Search Input: ", inputText);
      this.inputText = inputText;
    },
    refresh() {
      this.inputText = "";
      this.max = 50;
    },
  },
  computed: {
    filteredProducts() {
      return this.products.filter((item) => {
        const matchesPrice = item.price < Number(this.max);
        const matchesName = item.name
          .toLowerCase()
          .includes(this.inputText.toLowerCase());
        return matchesPrice && matchesName;
      });
    },
  },
};
</script>
