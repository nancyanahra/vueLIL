<template>
  <section class="container">
    <range-selector :products="filteredProducts" v-model="max" />

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
export default {
  name: "HomeView",
  data: function () {
    return {
      max: 50,
      cart: [],
      displayCart: false,
    };
  },
  props: ["products"],
  components: {
    Product,
    RangeSelector,
  },

  computed: {
    filteredProducts() {
      return this.products.filter((item) => item.price < Number(this.max));
    },
  },
};
</script>
