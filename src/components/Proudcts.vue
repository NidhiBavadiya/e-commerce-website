<template>
  <div>
          <!-- buttons -->
          <!-- <b-button @click="filterdata('S')" variant="dark" class="btn m-1" pill
            >S</b-button
          >
          <b-button @click="filterdata('M')" variant="dark" class="btn m-1" pill
            >M</b-button
          >
          <b-button @click="filterdata('L')" variant="dark" class="btn m-1" pill
            >L</b-button
          >
          <b-button
            @click="filterdata('XL')"
            variant="dark"
            class="btn m-1"
            pill
            >XL</b-button
          >
          <b-button
            @click="filterdata('XXL')"
            variant="dark"
            class="btn m-1"
            pill
            >XXL</b-button
          > -->



           <!-- radio button  -->
           <b-form-group v-slot="{ ariaDescribedby }">
            <b-form-radio
              v-model="selected"
              :aria-describedby="ariaDescribedby"
              name="some-radios"
              value="S"
              @change="small"
            >S</b-form-radio>
            <b-form-radio
              v-model="selected"
              :aria-describedby="ariaDescribedby"
              name="some-radios"
              value="M"
              @change="medium"
            >M</b-form-radio>
            <b-form-radio
              v-model="selected"
              :aria-describedby="ariaDescribedby"
              name="some-radios"
              value="L"
           
            >L</b-form-radio>
            <b-form-radio
              v-model="selected"
              :aria-describedby="ariaDescribedby"
              name="some-radios"
              value="XL"
     
            >XL</b-form-radio>
            <b-form-radio
              v-model="selected"
              :aria-describedby="ariaDescribedby"
              name="some-radios"
              value="XXL"
             
            >XXL</b-form-radio>
          </b-form-group>
</div>  
  
</template>

<script>
export default {
    data() {
        return {
            
        }
    },
    computed:{

    },
    methods:{
  // filterdata(val) {
        //   switch (val) {
    //     case 'S':
    //       console.log("ssss");
    //     this.small()
    //       break;
    //       case 'M':
    //       console.log("mmm");
    //       this.medium()
    //       break;
    //       case 'L':
    //       console.log("llll");

    //       break;
    //       case 'XL':
    //       console.log("xlxl");

    //       break;
    //       case 'XXL':
    //       console.log("xxl");

    //       break;
    //     default:
    //       break;
    //   }

    // },
    },
}
</script>

<style>

</style>