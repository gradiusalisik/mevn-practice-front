<template>
  <header class="header">
    <div class="header__left">
      <router-link to="/">
        Logo
      </router-link>
    </div>
    <div class="header__right">
      <router-link to="/cart"> Cart {{ cartCount }} </router-link>
      <ul class="nav">
        <li
          class="nav__link"
          v-for="({ id, title }, key) in categories"
          :key="key"
        >
          <router-link :to="`category/${id}`">{{ title }}</router-link>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
  export default {
    name: "MevnHeader",
    props: {
      categories: {
        type: Array,
        default: () => [],
      },
      cartCount: {
        type: Number,
        default: 0,
      },
    },
  };
</script>

<style lang="scss" scoped>
  .header {
    padding: 10px;
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid black;
  }

  .nav {
    display: flex;
    list-style: none;
    justify-content: space-between;
    width: 100%;
    padding-left: 0;

    &__link {
      margin-right: 10px;
      a {
        cursor: pointer;
        text-decoration: none;
        color: #000;
        transition: color 0.3s;

        &:hover {
          color: olive;
        }
      }
    }
  }
</style>
