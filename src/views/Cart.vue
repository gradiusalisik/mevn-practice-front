<template>
  <div class="cart">
    <template v-if="cartItems">
      <ul class="cart__list">
        <li class="cart__item" v-for="(item, key) in cartItems" :key="key">
          {{ item.title }} - <strong>
            {{ item.price }}$
            </strong>
        </li>
      </ul>
      <div class="cart__panel">
        Quantity: {{ cartCount }} Total: {{ cartTotalPrice }}
      </div>
    </template>
    <template v-else>
      <img src="https://images.pexels.com/photos/459762/pexels-photo-459762.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260" alt="empty" class="cart__image-empty">
      <p class="cart__empty">
        Your cart is empty please add items to it
      </p>
    </template>
  </div>
</template>

<script>
  import { mapGetters } from "vuex";
  export default {
    name: "Cart",
    computed: {
      ...mapGetters({
        cartItems: "cartItems",
        cartTotalPrice: "cartTotalPrice",
        cart: "cart",
        cartCount: "cartCount"
      }),
    },
  };
</script>

<style lang="scss" scoped>
  .cart {
    padding: 10px;

    &__list {
      padding-left: 0;
    }

    &__item {
      padding-top: 10px;
      padding-bottom: 10px;
      background-color: rgba(0, 0, 0, 0.1);

      &:not(:last-child) {
        border-bottom: 1px solid rgba(0, 0, 0, 0.2);
      }
    }

    &__panel {
      font-size: 24px;
    }

    &__image-empty {
      width: 500px;
    }

    &__empty {
      margin: 0;
      font-size: 24px;
      font-weight: bold;
    }
  }
</style>
