<template>
  <div id="basket-store">
    <h3>Mon panier :</h3>
    <p>Prix total de mon panier TTC : {{totalPriceTTC}} €</p>
    <p>Dernière modification : {{lastUpdateBasket}}</p>
    <div v-for="(product, index) in basket" :key="index">
      <span>{{product.name}} - {{product.price}} € </span>
      <button @click="removeProductInBasket(index)">enlever de mon panier</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BasketStore',
  data() {
    return {
      lastUpdateBasket: 'aucune modification'
    }
  },
  props: {
    basket: Array
  },
  methods: {
    removeProductInBasket(index) {
      this.$emit('removeProductEvent', index);
    }
  },
  computed: {
    totalPriceTTC() {
      return this.basket.length > 0
        ? this.basket
            .map(product => product.price * 1.2)
            .reduce((totalTTC, priceHT) => totalTTC + priceHT)
            .toFixed(2)
        : 0
    }
  },
  watch: {
    basket() {
      const date = new Date();
      this.lastUpdateBasket = `${date.getHours()}h${date.getMinutes()}m${date.getSeconds()}s`;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
