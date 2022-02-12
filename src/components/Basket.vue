<template>
  <v-container>
    <h1 class="text-center mb-3 green--text terxt--darken-4 font-weight-black">
      Payment
    </h1>
    <v-simple-table fixed-header height="300px">
      <template v-slot:default>
        <thead class="font-weight-black">
          <tr>
            <th class="blue darken-4 white--text">#</th>
            <th class="text-left blue darken-4 white--text">Name</th>
            <th class="text-left blue darken-4 white--text">Price</th>
            <th class="text-left blue darken-4 white--text">Amount</th>
            <th class="text-left blue darken-4 white--text">Total Price</th>
          </tr>
        </thead>
        <tbody class="font-weight-medium blue lighten-3">
          <tr v-for="(item, index) in productshop" :key="index">
            <td>{{ index + 1 }}</td>
            <td>{{ product[item.id - 1].title }}</td>
            <td>{{ item.price }} $</td>
            <td>{{ item.count }}</td>
            <td class="font-weight-black">{{ item.price * item.count }} $</td>
          </tr>
          <tr class="font-weight-black white--text indigo lighten-1">
            <td>##</td>
            <td class="text-center">Total</td>
            <td>{{ sumPriceofOne() }} $</td>
            <td>{{ sumCount() }}</td>
            <td>{{ sumPrice() }} $</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <div class="text-center pt-2">
      <v-btn color="primary" @click="PayAll(0)" class="mx-5 my-2">
        Pay All</v-btn
      >
    </div>
    <v-btn
      class="transition-swing v-btn v-btn--bottom v-btn--is-elevated v-btn--fab v-btn--fixed v-btn--has-bg v-btn--right v-btn--round theme--light v-size--large"
      fab
      dark
      large
      color="purple"
      @click="PayAll(1)"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="16"
        height="16"
        fill="currentColor"
        class="bi bi-arrow-left"
        viewBox="0 0 16 16"
      >
        <path
          fill-rule="evenodd"
          d="M15 8a.5.5 0 0 0-.5-.5H2.707l3.147-3.146a.5.5 0 1 0-.708-.708l-4 4a.5.5 0 0 0 0 .708l4 4a.5.5 0 0 0 .708-.708L2.707 8.5H14.5A.5.5 0 0 0 15 8z"
        />
      </svg>
      back
    </v-btn>
  </v-container>
</template>

<script>
export default {
  props: ["product", "productshop"],
  methods: {
    sumPrice() {
      let sum = 0;
      for (let i = 0; i < this.productshop.length; i++) {
        sum += this.productshop[i].price * this.productshop[i].count;
      }
      return sum;
    },
    sumPriceofOne() {
      let sum = 0;
      for (let i = 0; i < this.productshop.length; i++) {
        sum += this.productshop[i].price;
      }
      return sum;
    },
    sumCount() {
      let sum = 0;
      for (let i = 0; i < this.productshop.length; i++) {
        sum += this.productshop[i].count;
      }
      return sum;
    },
    PayAll(i) {
      this.$emit("PayAll", 2, i);
    },
  },
};
</script>

<style></style>
