<template>
  <div class="about">
    <table class="table m-auto bg-gray-200 border-2 border-white">
      <tr class="bg-blue-200 text-white">
        <td class="p-3">
          Country
        </td>
        <td class="p-3">
          Confirmed
        </td>
        <td class="p-3">
          Deaths
        </td>
        <td class="p-3">
          Recovered
        </td>
      </tr>
      <tr v-for="isi in countries" v-bind:key="isi.countries">
        <td class="border-2 border-white">
            {{isi.Country}}
          </td>
          <td class="border-2 border-white">
            {{isi.TotalConfirmed}}
          </td>
          <td class="border-2 border-white">
            {{isi.TotalDeaths}}
          </td>
          <td class="border-2 border-white">
            {{isi.TotalRecovered}}
          </td>
      </tr>
    </table>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'About',
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
