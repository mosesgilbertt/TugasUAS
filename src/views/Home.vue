<template>
  <div class="home">
  <div class="flex space-x-4 p-3">
      <div class="flex-1 bg-yellow-400 border-4 p-3 rounded-l-lg">
      Total Confirmed <br>
      {{global.TotalConfirmed}}
      </div>
      <div class="flex-1 bg-yellow-200 border-4 p-3">
      Total Deaths <br>
      {{global.TotalDeaths}}
      </div>
      <div class="flex-1 bg-yellow-400 border-4 p-3 rounded-r-lg">
      Total Recovered <br>
      {{global.TotalRecovered}}
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
   name: 'Home',
  data () {
    return {
      id: null,
      global: {},
      countries:[]
    }
  },
  mounted ()
  {
    const axios = require('axios');
    axios.get('https://api.covid19api.com/summary')
    .then(resp =>{
      if(resp && resp.status && resp.status == 200)
      {
        this.id = resp && resp.data && resp.data.ID;
        this.global = resp && resp.data && resp.data.Global;
        this.countries = resp && resp.data && resp.data.Countries;
      }
    })
    .catch(err => {
      console.log(err)
    });
  }
}
</script>
