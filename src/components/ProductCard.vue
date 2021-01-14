<template>
  <div class="card">
    <div
      class="card__banner"
      :style="`background-image: url(${imageUrl})`"
    ></div>
    <h2 class="card__title">{{ title }}</h2>
    <div class="card__footer">
      <p class="card__description">{{ description }}</p>
      <span class="card__price">{{ price }}$</span>
      <button v-if="!inCart" class="card__button" @click="$emit('add-to-cart')">
        Добавить в корзину
      </button>
      <button
        v-else
        class="card__button card__button_delete"
        @click="$emit('add-to-cart')"
      >
        Убрать из корзины
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "ProductCard",
    props: {
      title: {
        type: String,
        default: "",
      },
      description: {
        type: String,
        default: "",
      },
      price: {
        type: Number,
        default: 0,
      },
      imageUrl: {
        type: String,
        default: "",
      },
      inCart: {
        type: Boolean,
        default: false,
      },
    },
  };
</script>

<style lang="scss" scoped>
  .card {
    position: relative;
    width: 33.333%;
    height: 300px;
    padding: 20px;
    margin: 10px;
    border: 1px solid black;
    border-radius: 12px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    overflow: hidden;

    &__title {
      position: relative;
      z-index: 1;
      font-size: 30px;
      color: #fff;
    }

    &__banner {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center;

      &::before {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        content: "";
        background-color: rgba(0, 0, 0, 0.3);
      }
    }

    &__description {
      font-size: 14px;
      color: #fff;
      margin-bottom: 10px;
      max-height: 80px;
      overflow: hidden;
    }

    &__price {
      margin-bottom: 10px;
      display: block;
      font-size: 20px;
      color: #fff;
      text-shadow: red;
    }

    &__footer {
      position: relative;
    }

    &__button {
      max-width: 200px;
      width: 100%;
      height: 40px;
      border: none;
      border-radius: 24px;
      text-transform: uppercase;
      font-size: 12px;
      color: #fff;
      background-color: #365b8e;
      cursor: pointer;
      transition: background-color 0.3s;

      &:hover {
        background-color: #173156;
      }

      &_delete {
        background-color: #8e3636;

        &:hover {
          background-color: #c72222;
        }
      }
    }
  }
</style>
