<template>
  <v-container>
    <h1 class="text-center mb-3 brown--text terxt--darken-4 font-weight-black">
      Product Details
    </h1>

    <div class="d-flex justify-center">
      <v-card
        elevation="10"
        class="mx-5"
        min-width="400px"
        max-width="90%"
        min-height="500px"
      >
        <v-row>
          <v-col cols="12" md="5" sm="12" class="ml-5">
            <img
              :src="product[productid - 1].image"
              height="450px"
              width="400px"
              alt=""
          /></v-col>
          <v-col cols="12" md="6" sm="12">
            <v-card-title>
              <h1>{{ product[productid - 1].title }}</h1>
            </v-card-title>
            <v-card-text>
              <h3>{{ product[productid - 1].description }}</h3>
            </v-card-text>

            <v-card-text class="text--primary">
              <div class="d-flex mb-2">
                <h2 class="mr-2">Rating :</h2>
                <h2 class="light-green--text accent-3">
                  {{ product[productid - 1].rating.rate }}
                </h2>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  fill="currentColor"
                  class="bi bi-star-fill yellow--text text--darken-4 mx-2"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"
                  />
                </svg>
              </div>
              <div class="d-flex">
                <h2>Buy :</h2>
                <h2 class="mx-2 deep-orange--text text--darken-3">
                  {{ product[productid - 1].rating.count }}
                </h2>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  fill="currentColor"
                  class="bi bi-people-fill deep-purple--text text--darken-3"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M7 14s-1 0-1-1 1-4 5-4 5 3 5 4-1 1-1 1H7zm4-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"
                  />
                  <path
                    fill-rule="evenodd"
                    d="M5.216 14A2.238 2.238 0 0 1 5 13c0-1.355.68-2.75 1.936-3.72A6.325 6.325 0 0 0 5 9c-4 0-5 3-5 4s1 1 1 1h4.216z"
                  />
                  <path d="M4.5 8a2.5 2.5 0 1 0 0-5 2.5 2.5 0 0 0 0 5z" />
                </svg>
              </div>
            </v-card-text>
            <v-card-title
              ><h2 class="indigo--text text--darken-1">
                {{ product[productid - 1].price }} $
              </h2></v-card-title
            >
            <v-col cols="12" md="6" sm="12" class="mb-5">
              <v-row align="center" justify="center">
                <v-btn
                  style="height: 55px"
                  class="red--text text--darken-4"
                  @click="productcount <= 0 ? productcount : productcount--"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="20"
                    height="20"
                    fill="currentColor"
                    class="bi bi-dash-circle"
                    viewBox="0 0 16 16"
                  >
                    <path
                      d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"
                    />
                    <path
                      d="M4 8a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7A.5.5 0 0 1 4 8z"
                    />
                  </svg>
                </v-btn>
                <div>
                  <v-text-field
                    :value="productcount"
                    style="width: 50px; height: 55px"
                    outlined
                    oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');"
                  ></v-text-field>
                </div>
                <v-btn
                  style="height: 55px"
                  class="blue--text text--darken-4"
                  @click="productcount++"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="20"
                    height="20"
                    fill="currentColor"
                    class="bi bi-plus-circle"
                    viewBox="0 0 16 16"
                  >
                    <path
                      d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"
                    />
                    <path
                      d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4z"
                    />
                  </svg>
                </v-btn>
                <v-btn
                  style="height: 55px"
                  color="success"
                  class="black--text"
                  @click="getcount(1)"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="30"
                    height="30"
                    fill="currentColor"
                    class="bi bi-cart-check"
                    viewBox="0 0 16 16"
                  >
                    <path
                      d="M11.354 6.354a.5.5 0 0 0-.708-.708L8 8.293 6.854 7.146a.5.5 0 1 0-.708.708l1.5 1.5a.5.5 0 0 0 .708 0l3-3z"
                    />
                    <path
                      d="M.5 1a.5.5 0 0 0 0 1h1.11l.401 1.607 1.498 7.985A.5.5 0 0 0 4 12h1a2 2 0 1 0 0 4 2 2 0 0 0 0-4h7a2 2 0 1 0 0 4 2 2 0 0 0 0-4h1a.5.5 0 0 0 .491-.408l1.5-8A.5.5 0 0 0 14.5 3H2.89l-.405-1.621A.5.5 0 0 0 2 1H.5zm3.915 10L3.102 4h10.796l-1.313 7h-8.17zM6 14a1 1 0 1 1-2 0 1 1 0 0 1 2 0zm7 0a1 1 0 1 1-2 0 1 1 0 0 1 2 0z"
                    />
                  </svg>
                </v-btn> </v-row
            ></v-col>
          </v-col>
        </v-row>
      </v-card>
    </div>
    <v-btn
      class="transition-swing v-btn v-btn--bottom v-btn--is-elevated v-btn--fab v-btn--fixed v-btn--has-bg v-btn--right v-btn--round theme--light v-size--large"
      fab
      dark
      large
      color="green"
      @click="getcount(0)"
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
  props: ["product"],
  data() {
    return {
      toggle_exclusive: undefined,
      productid: this.$route.params.id,
      productcount: 0,
    };
  },
  methods: {
    getcount(i) {
      if (i == 1) {
        this.$emit("getcount", 2, this.productid, this.productcount);
        this.productcount = 0;
      } else {
        this.$emit("getcount", 2, this.productid, -1);
        this.productcount = 0;
      }
    },
  },
};
</script>

<style></style>
