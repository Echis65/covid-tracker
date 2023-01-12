<template>
 <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate"/>
    <DataCards :newConfirmed="stats.NewConfirmed" :totalConfirmed="stats.TotalConfirmed" :newDeaths="stats.NewDeaths" :totalDeaths="stats.TotalDeaths"/>
    <CountrySelect :countries="countries"/>
 </main>

 <main v-else class="flex align-center justify-center flex-col">
    <div class="text-gray-500 text-center mt-10 text-3xl">
      Fetching Data... 
    </div>
    <div >
      <iframe  src="https://giphy.com/embed/jAYUbVXgESSti" width="250" height="200" frameBorder="0" class="giphy-embed m-auto" allowFullScreen></iframe>
    </div>
 </main>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
import DataTitle from "@/components/DataTitle.vue"
import DataCards from '@/components/DataCards.vue';
import CountrySelect from '@/components/CountrySelect.vue';

export default {
  name: "HomeView",
  components: {
    DataTitle,
    DataCards,
    CountrySelect,
  },
  data(){
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      countries: [],
      stats: {}
    }
  },
  methods: {
    async fetchCovidData () {
      const res = await axios.get("https://api.covid19api.com/summary")
      if(res.status === 200){
        return res.data
      }
    }
  },
  async created() {
      const data =  await this.fetchCovidData()
      console.log(data)
      this.dataDate = data.Date
      this.stats = data.Global
      this.countries = data.Countries
      this.loading = false
  } 
};
</script>
