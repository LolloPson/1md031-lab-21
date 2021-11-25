<template>




  <div id = "burger" class="burger" style="float:left;  ">


    <h3>  {{burger.name}}</h3>


    <img v-bind:src="burger.url" alt="" style="margin-right: 15px; height: 300px; width: 300px">

    <h4>{{ "Ingredients" }}</h4>

    <ul>

      <li> {{ burger.calories}} kCal </li>
      <li v-if="burger.lactose"> Contains <span class="ingredient"> lactose </span></li>
      <li v-if="burger.gluten"> Contains <span class="ingredient"> gluten </span></li>


    </ul>
    <div>
      <button v-on:click="decreaseBurger" class="numberOfBurgers">
        -
      </button>

      <button v-on:click="increaseBurger" class="numberOfBurgers">
        +
      </button>
      <p>Amount: {{ amountOrdered }} </p>
    </div>


  </div>




</template>

<script>
export default {
  name: 'Burger',
  props: {
    burger: Object

  },
  data: function () {
    return {
      amountOrdered: 0,
    }
  },

  methods: {
    increaseBurger: function () {
      this.amountOrdered++
      this.$emit('orderedBurger', {
        name: this.burger.name,
            amount: this.amountOrdered
          }
      );
    },
    decreaseBurger: function () {
      this.amountOrdered--
      this.$emit('orderedBurger', {
        name: this.burger.name,
            amount: this.amountOrdered
          }
      );
    }
  }
}





</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


.wrapper {
  display: grid;
  grid-template-columns: auto auto auto;
  column-gap: 50px;
  justify-items: center;
  float: left;
}
.box {

}

.a {
  grid-column: 1;
  grid-row:1;

;

}
.ingredient{
  font-weight: bold;
}





</style>
