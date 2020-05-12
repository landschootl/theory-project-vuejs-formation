<template>
  <div id="manage-store">
    <h3>Administration du magasin</h3>
    <button @click="openOrCloseStore()">{{store.open ? 'Fermer' : 'Ouvrir'}} le magasin</button>
    <p>Nom du magasin : <input type="text" v-model="store.name"/></p>
    <p>Magasin ouvert : <input type="checkbox" v-model="store.open"/></p>
  </div>
</template>

<script>
export default {
  name: 'ManageStore',
  props: {
    store: Object,
  },
  methods: {
    openOrCloseStore() {
      this.store.open = !this.store.open;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #manage-store {
    background-color: aliceblue;
    padding: 10px;
  }
</style>
