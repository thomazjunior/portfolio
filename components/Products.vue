<template>
  <div>
    <div class="card-image">
      <figure class="image is-4by3">
        <img :src="product.url" alt="Placeholder image" />
      </figure>
    </div>
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4">{{ product.title }}</p>
        </div>
      </div>
      <div class="content is-clearfix">
        <p>{{ product.description }}</p>
      </div>
    </div>

    <nuxt-link
      class="details"
      :to="{
        name: 'product_detail-id',
        params: {
          id: product.id,
          url: product.url,
          title: product.title,
          reviews: product.reviews,
          isAddedBtn: product.isAddedBtn,
        },
      }"
    >
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: "products",
  props: ["product"],

  data() {
    return {
      addToCartLabel: "Add to cart",
      viewDetailsLabel: "Details",
      selected: 1,
      quantityArray: [],
    };
  },

  mounted() {
    for (let i = 1; i <= 20; i++) {
      this.quantityArray.push(i);
    }

    if (this.$props.product.quantity > 1) {
      this.selected = this.$props.product.quantity;
    }
  },

  computed: {
    isUserLogged() {
      return this.$store.getters.isUserLoggedIn;
    },
  },

  methods: {
    addToCart(id) {
      let data = {
        id: id,
        status: true,
      };
      this.$store.commit("addToCart", id);
      this.$store.commit("setAddedBtn", data);
    },
    removeFromCart(id) {
      let data = {
        id: id,
        status: false,
      };
      this.$store.commit("removeFromCart", id);
      this.$store.commit("setAddedBtn", data);
    },
    onSelectQuantity(id) {
      let data = {
        id: id,
        quantity: this.selected,
      };
      this.$store.commit("quantity", data);
    },
  },
};
</script>

<style lang="scss" scoped>
.details {
  cursor: pointer;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;

  &:hover {
    border: 1px solid #51bafc;
  }
}
.button,
.select {
  z-index: 2;
}
.select {
  position: absolute;
  right: 15px;
  bottom: 35px;
}
.card-content {
  padding: 0;
}
.buttons {
  margin: 0;
}
</style>


