<template>
   <div class="Boton">
      <!--<input
         type="button"
         v-model="value"
         :style="{
            width: spanX * 45 + 2 * (spanX - 1),
            height: spanY * 45 + 2 * (spanY - 1),
         }"
         @click="PasarValor()"
      />-->
      <input
         type="button"
         v-model="value"
         :style="[
            spanX === 1 ? { width: '45px' } : { width: '92px' },
            spanY === 1 ? { height: '45px' } : { height: '92px' },
         ]"
         @click="PasarValor()"
      />
   </div>
</template>

<script>
   export default {
      name: "Boton",
      props: {
         msg: String,
      },
      data() {
         return {
            value: Number,
            spanX: Number,
            spanY: Number,
            click_count: 1,
         };
      },
      methods: {
         PasarValor() {
            console.log(this.value);
            if (this.value === 1) {
               this.value = 2;
            } else {
               this.value = 1;
            }
            switch (this.click_count) {
               case 1:
                  this.spanY = 1;
                  break;
               case 2:
                  this.spanX = 2;
                  break;
               case 3:
                  this.spanX = 1;
                  this.spanY = 2;
                  this.click_count = 0;
                  break;
            }
            this.click_count++;
         },
      },
      beforeCreate() {
         console.log("beforeCreate");
      },
      created() {
         this.value = 1;
         this.spanX = 1;
         this.spanY = 2;
         console.log("created");
      },
      beforeMount() {
         console.log("beforeMount");
      },
      mounted() {
         console.log("mounted");
      },
      beforeUpdate() {
         console.log("beforeUpdate");
      },
      updated() {
         console.log("update");
      },
      beforeUnmount() {
         console.log("beforeDestroy");
      },
      unmounted() {
         console.log("unmounted");
      },
   };
</script>

<style scoped>
   input {
      /*width: 45 * spanX + "px";
      height: 45 * spanY + "px";*/
      width: 45px;
      height: 45px;
      size: 18px;
      font-weight: bold;
      margin: 2px;
   }
</style>
