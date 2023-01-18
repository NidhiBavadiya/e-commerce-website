<template>
  <div>
    <b-row>
      <b-col md="1" class="pt-5 ps-4">
        <div class="d-flex flex-column justify-content-center">
          <!-- check box -->
          <b-form-group
            v-slot="{ ariaDescribedby }"
          >
            <b-form-checkbox-group
              v-model="selected"
              :options="options"
              :aria-describedby="ariaDescribedby"
              @change="small"
              stacked
              buttons
              class="cbtn"
            ></b-form-checkbox-group>
          </b-form-group>

          <div class="mt-3">
            Selected: <strong>{{ selected }}</strong>
          </div>
          <!--  -->
        </div>
        <!--  -->
      </b-col>
      <b-col md="11" class="p-4">
        <b-row>
          <b-col
            cols="3"
            class="mt-4"
            v-for="product in Products"
            :key="product.id"
          >
            <b-card class="position-relative">
              <div
                class="position-absolute bg-dark text-light end-0 p-1"
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
            </b-card>
          </b-col>
        </b-row>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import { BCol, BRow, BCard, BImg, BFormGroup, BFormRadio,BFormCheckboxGroup } from "bootstrap-vue";
// import exp from "constants";
import data from "../assets/data.json";
export default {
  component: {
    BCol,
    BRow,
    BCard,
    BImg,
    BFormGroup,
    BFormRadio,
    BFormCheckboxGroup,
  },
  data() {
    return {
      image: null,
      title: "",
      size: "",
      price: "",

      data: data,
      Products: data.products,
      selected: [], 

      options: [
        { text: "S", value: "S" },
        { text: "M", value: "M" },
        { text: "L", value: "L" },
        { text: "XL", value: "XL" },
        { text: "XXL", value: "XXL" },
      ],
      duplicate: [],
    };
  },

  methods: {
    small() {
      console.log("jaimi", this.selected);
      this.Products.forEach((element, index) => {
        console.log(element.availableSizes);
        let same = false;

        element.availableSizes.forEach((el) => {
          console.log("el", el);
          console.log("jaimi", this.selected);
          if (el == this.selected) {
            same = true;
          }
        });
        if (same) {
          console.log(index);
          this.duplicate.push(element);
          this.Products = this.duplicate;
          console.log("duplicate", this.Products);
       
        }
      });
    },
  },
};
</script>



