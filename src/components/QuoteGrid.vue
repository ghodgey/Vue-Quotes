<template>

  <div class="row">
    <!-- native => notifies that app-quote can be clicked and it will registe rthe click of the app-quote component -->
      <app-quote v-for="(quote, index) in quotes" :key="quote" @click.native="deleteQuote(index)">{{ quote }}</app-quote> 
  </div>
        
</template>


<script>
import Quote from "./Quote.vue";

export default {
  props: ["quotes"],
  components: {
    "app-quote": Quote
  },
  methods: {
    deleteQuote(index) {
      this.$emit('quoteDeleted', index)
    }
  }
};
</script>

<style>
</style>
