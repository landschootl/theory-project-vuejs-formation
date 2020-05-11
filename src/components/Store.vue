<template>
  <div class="store">
    <img src="https://img.pngio.com/shop-icon-png-175739-free-icons-library-store-icon-png-1024_1024.jpg" id="img-store"/>
    <h1>{{fullName}}</h1>
    <h2 class="store-open" v-if="store.open">Magasin : Open</h2>
    <h2 class="store-close" v-else>Magasin : Close</h2>
    <manage-store :store="store"></manage-store>
  </div>
</template>

<script>
import ManageStore from "./ManageStore";

export default {
  name: 'Store',
  components: {
    ManageStore
  },
  data() {
    return {
      store: {
        name: 'Fred',
        open: false
      }
    }
  },
  computed: {
    fullName() {
      return `Magasin de ${this.store.name}`
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
</style>
