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
            <th class="text-left blue darken-4 white--text">Delete</th>
          </tr>
        </thead>
        <tbody class="font-weight-medium blue lighten-3">
          <tr v-for="(item, index) in productshop" :key="index">
            <td>{{ index + 1 }}</td>
            <td>{{ product[item.id - 1].title }}</td>
            <td>{{ item.price }} $</td>
            <td>{{ item.count }}</td>
            <td class="font-weight-black">{{ item.price * item.count }} $</td>
            <td>
              <v-btn
                color="red"
                @click="removeproduct(index)"
                class="mx-5 my-2"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  fill="currentColor"
                  class="bi bi-trash3"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M6.5 1h3a.5.5 0 0 1 .5.5v1H6v-1a.5.5 0 0 1 .5-.5ZM11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3A1.5 1.5 0 0 0 5 1.5v1H2.506a.58.58 0 0 0-.01 0H1.5a.5.5 0 0 0 0 1h.538l.853 10.66A2 2 0 0 0 4.885 16h6.23a2 2 0 0 0 1.994-1.84l.853-10.66h.538a.5.5 0 0 0 0-1h-.995a.59.59 0 0 0-.01 0H11Zm1.958 1-.846 10.58a1 1 0 0 1-.997.92h-6.23a1 1 0 0 1-.997-.92L3.042 3.5h9.916Zm-7.487 1a.5.5 0 0 1 .528.47l.5 8.5a.5.5 0 0 1-.998.06L5 5.03a.5.5 0 0 1 .47-.53Zm5.058 0a.5.5 0 0 1 .47.53l-.5 8.5a.5.5 0 1 1-.998-.06l.5-8.5a.5.5 0 0 1 .528-.47ZM8 4.5a.5.5 0 0 1 .5.5v8.5a.5.5 0 0 1-1 0V5a.5.5 0 0 1 .5-.5Z"
                  /></svg
              ></v-btn>
            </td>
          </tr>
          <tr class="font-weight-black white--text indigo lighten-1">
            <td>##</td>
            <td class="text-center">Total</td>
            <td>{{ sumPriceofOne() }} $</td>
            <td>{{ sumCount() }}</td>
            <td>{{ sumPrice() }} $</td>
            <td></td>
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
    removeproduct(index) {
      this.productshop.splice(index, 1);
    },
  },
};
</script>

<style></style>
