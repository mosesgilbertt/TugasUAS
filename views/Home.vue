<template>
  <div class="home">
  <div  v-for="item in list" class="flex space-x-4">
      <div class="flex-1 bg-blue-200 border-4">
      Total Confirmed <br>
      {{item.TotalConfirmed}}
      </div>
      <div class="flex-1 ...">
      Total Deaths <br>
      {{item.TotalDeaths}}
      </div>
      <div class="flex-1 ...">
      Total Recovered <br>
      {{item.TotalRecovered}}
      </div>
    </div>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'App',
  data() {
    return {list:['Global']}
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
