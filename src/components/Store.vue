<template>
  <div id="store">
    <div class="bloc">
      <div class="sub-bloc">
        <img src="https://img.pngio.com/shop-icon-png-175739-free-icons-library-store-icon-png-1024_1024.jpg" id="img-store"/>
        <h1>{{fullName}}</h1>
        <h2 class="store-open" v-if="store.open">Magasin : Open</h2>
        <h2 class="store-close" v-else>Magasin : Close</h2>
        <manage-store :store="store"></manage-store>
      </div>
      <div class="sub-bloc">
        <CatalogStore @addProductEvent="addProductInBasket($event)"></CatalogStore>
        <BasketStore :basket="basket" @removeProductEvent="removeProductInBasket($event)"></BasketStore>
      </div>
    </div>
  </div>
</template>

<script>
import ManageStore from "./ManageStore";
import CatalogStore from "./CatalogStore";
import BasketStore from "./BasketStore";

export default {
  name: 'Store',
  components: {
    ManageStore,
    CatalogStore,
    BasketStore
  },
  data() {
    return {
      store: {
        name: 'Fred',
        open: false
      },
      basket: []
    }
  },
  computed: {
    fullName() {
      return `Magasin de ${this.store.name}`
    }
  },
  methods: {
    addProductInBasket(product) {
      this.basket.push(product);
    },
    removeProductInBasket(index) {
      this.basket.splice(index, 1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .store-open {
    color: green;
  }
  .store-close {
    color: red;
  }
  #img-store {
    width: 30%;
  }
  #store {
    height: 100%;
  }
  .bloc {
    width: calc(50vw - 43px);
    float: left;
    margin: 12px;
    border: thick double #32a1ce;
  }
  .sub-bloc {
    width: calc(25vw - 52px);
    float: left;
    margin: 15px;
  }
</style>
