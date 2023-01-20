        
<template>
  <div>
    <!-- cart icon button -->
    <show-cart :isActive="showCart" :carts="carts"></show-cart>
    <b-row class="justify-content-end">
      <b-col md="1" class="mt-3">
        <div class="position-relative">
          <b-button @click="displayCart" variant="dark" class="w-75 p-3">
            <b-badge
              variant="light"
              class="position-absolute top-0 right-0 bg-light text-dark"
              >1</b-badge
            >
            <b-icon icon="cart4" class="m-0" aria-hidden="true"></b-icon>
          </b-button>
        </div>
      </b-col>
    </b-row>
    <b-row>
      <b-col md="1" class="pt-4 ps-4">
        <div class="d-flex flex-column justify-content-center">
          <!-- check box -->
          <b-form-group v-slot="{ ariaDescribedby }">
            <b-form-checkbox-group
              v-model="checked"
              :options="options"
              :aria-describedby="ariaDescribedby"
              @change="selectsize"
              stacked
              buttons
              class="cbtn"
            ></b-form-checkbox-group>
          </b-form-group>

          <div class="mt-3">
            checked: <strong>{{ checked }}</strong>
          </div>
        </div>
      </b-col>
      <!-- product card -->
      <b-col md="11">
        <b-row>
          <b-col
            cols="3"
            class="mt-4"
            v-for="product in paginatedCards"
            :key="product.id"
          >
            <b-card class="position-relative p-3" id="productcard">
              <div
                class="position-absolute bg-dark text-light end-0 top-0 p-1"
                v-if="product.FreeShipping"
              >
                FreeShipping
              </div>
              <b-img
                :src="product.image"
                class="h310"
                fluid
                alt="Responsive image"
              ></b-img>
              <p class="fw-bold product-title text-center">
                {{ product.title }}
              </p>
              <p class="text-center">{{ product.size }}</p>
              <p class="text-center">{{ product.price }}</p>
              <p class="text-center">or 5*$5.89</p>
              <b-button class="cartbtn" @click="addToCart(product)">Add To Cart</b-button>
            </b-card>
          </b-col>
        </b-row>
        <!-- pagination -->
        <b-pagination
          v-model="currentPage"
          :total-rows="rows"
          :per-page="perPage"
          aria-controls="productcard"
        ></b-pagination>
        <!--  -->
      </b-col>
    </b-row>
  </div>
</template>
  
<script>
import {
  BCol,
  BRow,
  BCard,
  BImg,
  BIcon,
  BBadge,
  BButton,
  BFormGroup,
  BFormRadio,
  BPagination,
  BFormCheckboxGroup,
} from "bootstrap-vue";
import showCart from "../components/ShowCart.vue";
import data from "../assets/data.json";
import ShowCart from "../components/ShowCart.vue";
export default {
  components: { ShowCart },
  component: {
    BCol,
    BRow,
    BCard,
    BImg,
    BIcon,
    BBadge,
    BButton,
    BFormGroup,
    BFormRadio,
    BPagination,
    BFormCheckboxGroup,
    showCart,
  },
  data() {
    return {
      perPage: 8,
      currentPage: 1,
      isActive: false,
      id:'',

      data: data,
      Products: data.products,
      checked: [],
      options: [
        { text: "S", value: "S" },
        { text: "M", value: "M" },
        { text: "L", value: "L" },
        { text: "XL", value: "XL" },
        { text: "XXL", value: "XXL" },
      ],
      newArray: [],
      carts:[],
      isClicked: null,
      showCart:false
    };
  },

  mounted() {
    this.newArray = this.Products;
  },

  computed: {
    rows() {
      return this.Products.length;
    },

    paginatedCards() {
      const { currentPage, perPage } = this;
      const start = (currentPage - 1) * perPage;
      const end = currentPage * perPage;

      return this.newArray.slice(start, end);
    },
  },

  methods: {
    // product size select function
    selectsize() {
      if (this.checked.length) {
        this.currentPage = 1;
        let arr = [];
        this.checked.forEach((check) => {
          this.Products.forEach((product) => {
            product.availableSizes.forEach((size) => {
              if (size == check) {
                let same = false;

                arr.forEach((a) => {
                  if (a.id == product.id) {
                    same = true;
                  }
                });
                if (!same) {
                  arr.push(product);
                }
              }
            });
          });
        });
        this.newArray = arr;
      } else {
        this.newArray = this.Products;
      }
    },
    addToCart(id) {
      console.log("id_data",id);
      this.carts.push(id)
      console.log("carts",this.carts);
      
    },
    displayCart() {
      this.showCart = !this.showCart;
    },
  },
};
</script>
  
  
  