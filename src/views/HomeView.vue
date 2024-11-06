<template>
  <section class="container">
    <search-bar :products="filteredProducts" @search="handleSearch" />
    <category-tag
      :selected-tags="selectedTags"
      @update:selected-tags="updateTags"
    />
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
import { ref, computed } from "vue";
import Product from "@/components/Product";
import RangeSelector from "@/components/RangeSelector";
import SearchBar from "@/components/SearchBar";
import CategoryTag from "@/components/CategoryTag";
export default {
  name: "HomeView",
  props: ["products"],
  components: {
    Product,
    RangeSelector,
    SearchBar,
    CategoryTag,
  },
  setup(props) {
    const max = ref(50);
    const cart = ref([]);
    const displayCart = ref(false);
    const inputText = ref("");
    const selectedTags = ref([]);

    const handleSearch = (searchText) => {
      console.log("Search Input: ", searchText);
      inputText.value = searchText;
    };

    const updateTags = (tags) => {
      if (Array.isArray(tags)) {
        selectedTags.value = tags;
      } else {
        selectedTags.value = [];
      }
    };

    const filteredProducts = computed(() => {
      return props.products.filter((item) => {
        const matchesPrice = item.price < Number(max.value);
        const matchesName = item.name
          .toLowerCase()
          .includes(inputText.value.toLowerCase());
        const matchesCategory =
          selectedTags.value.length === 0 ||
          selectedTags.value.includes(item.category);

        return matchesPrice && matchesName && matchesCategory;
      });
    });
    return {
      max,
      cart,
      displayCart,
      inputText,
      selectedTags,
      updateTags,
      handleSearch,
      filteredProducts,
    };
  },
};
</script>
