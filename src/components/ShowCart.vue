<template>
  <div>
    <b-sidebar :id="s_id" sidebar-class="border-right border-danger" :visible = "isActive">
     
      <b-row v-if="carts.length > 0">
          <b-col
            cols="12"
            v-for="cart in carts" :key="cart.id"
          >
      <b-card class="position-relative p-3" id="productcard">
        <b-row>
          <b-col cols="4">
              <b-img
              :src="cart.image"
                class="s_size"  
                fluid
                alt="Responsive image"
              ></b-img>
            </b-col>
            <b-col cols="8">
              <p class="fw-bold">{{ cart.title }}</p>
              <p class="">{{ cart.size }}</p>
              <p class="">{{ cart.price }}</p>
              <b-button @click="deleteCart(cart)" class="mt-4" variant="dark">Remove From Cart</b-button>
            </b-col>
            </b-row>
            </b-card>
            </b-col>
            </b-row>
            <b-row v-else> <h3 class="text-center mt-5">Cart is Empty</h3></b-row>
    </b-sidebar>
  </div>
</template>

<script>
import { BImg,BCol, BSidebar, BButton } from "bootstrap-vue";
import data from "../assets/data.json"
export default {
  components: {
 
    BSidebar,
    BButton,
    BImg,
    BCol
  },
  props: {
    s_id:String,
    carts:Array,
  isActive: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      id:'',
      data:data,
      Products:data.products
    }
  },
  methods:{
    deleteCart(item){
      console.log("dalete",item);
      this.carts.splice(item, 1);
      item.cart = false
    }
  }
};
</script>

<style>
</style>