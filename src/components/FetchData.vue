<template> 
  <div v-if="!data">Loading...</div>
  <p v-else>Current Bitcoin Price = USD${{ data.bpi.USD.rate }}</p>
</template>

<script>
  export default {
    data() {
      return {
        data: null,
      };
    },
    methods: {
      async fetchData() {      
        const response = await fetch("https://api.coindesk.com/v1/bpi/currentprice.json");      
        this.data = await response.json();
      },    
    },
    mounted() {
      this.fetchData();
    },
  };
</script>