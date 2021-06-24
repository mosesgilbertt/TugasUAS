<template>
  <div class="about">
    <table>
      <tr>
        <td>
          Country
        </td>
        <td>
          Confirmed
        </td>
        <td>
          Deaths
        </td>
        <td>
          Recovered
        </td>
      </tr>
      <tr v-for="isi in lst" v-bind:key="isi.id">
        <td>
            {{isi.Country}}
          </td>
          <td>
            {{isi.TotalConfirmed}}
          </td>
          <td>
            {{isi.TotalDeaths}}
          </td>
          <td>
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
  data() {
    return {lst:['Countries']}
  },
  mounted()
  {
    axios.get('https://api.covid19api.com/summary').then((resp) => {
      this.list=resp.data;
      console.warn(resp.data)
      })
      }
}
</script>
