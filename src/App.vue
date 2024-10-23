<template>
  <navbar :cart="cart" />
  <div class="container"></div>
  <router-view :cart="cart" @addToCart="addToCart" />
</template>

<script>
import Navbar from "@/components/Navbar";

export default {
  data: function () {
    return {
      cart: [],
      displayCart: false,
    };
  },
  components: {
    Navbar,
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
      if (this.cartTotal >= 100) {
        this.salesBtn = "btn-danger";
      }
    },
  },
};
</script>

<style lang="scss">
$primary: #6f42c1;

app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

@import "node_modules/bootstrap/scss/bootstrap";

.products-enter-active,
.products-leave-active {
  transition: all 0.5s ease-in-out;
}

.products-enter-from {
  opacity: 0;
  transform: translateX(300px);
}

.products-leave-to {
  opacity: 0;
  transform: translateX(-300px);
}
</style>
