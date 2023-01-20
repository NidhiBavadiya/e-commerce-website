<template>
  <div>
    <!-- <b-button v-b-toggle.sidebar-border>Toggle Sidebar</b-button> -->
    <b-sidebar id="sidebar-border" sidebar-class="border-right border-danger" :visible = "isActive">
     
      <b-row>
          <b-col
            cols="12"
            class="mt-4"
            v-for="cart in carts" :key="cart.id"
          >
      <b-card class="position-relative p-3" id="productcard">
        <b-row>
          <b-col>
              <b-img
              :src="cart.image"
                class="h310"
                fluid
                alt="Responsive image"
              ></b-img>
            </b-col>
            <b-col cols="4">
              <p class="fw-bold">{{ cart.title }}</p>
              <p class="">{{ cart.size }}</p>
              <p class="">{{ cart.price }}</p>
            </b-col>
             </b-row>
             <b-row>
              <b-col>
                <b-button @click="deleteCart(id)" dark>Delete</b-button>
              </b-col>
             </b-row>
            </b-card>
            </b-col>
            </b-row>
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
    deleteCart(id){
      console.log("dalete",id);
      this.carts.splice(id, 1);
      console.log(id);
    }
  }
};
</script>

<style>
</style>