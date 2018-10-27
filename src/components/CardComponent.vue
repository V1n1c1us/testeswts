<template>
   <div>
      <div  v-for="(people, index) in peoples" :key="index">
         Nome: {{people.name }}<br>
         Altura: {{ people.height}}<br>
         Sexo: {{ people.gender}}<br>
         Massa: {{ people.mass}}<br>
         Home: {{people.homeworld}}
         <hr>
      </div>
      <!--<button @click="previous" v-if="api.revious">Previous</button> - -->
      <!--<button @click="next" v-if="api.next">Next</button>-->

   </div>
</template>

<script>
	/* eslint-disable no-mixed-spaces-and-tabs,no-console */
   import axios from 'axios'
	export default {
		name: "CardComponent",
        data() {
			return {
				peoples: { },
                films: { },
                planets: [],
            }
        },

        created() {
            this.getPeoples()
        },
        methods: {
			getPeoples(){
				var vm = this
				this.axios.all([
					axios.get("https://swapi.co/api/people/"),
					axios.get("https://swapi.co/api/planets/1")
				]).then(response => {
                    vm.peoples = response[0].data.results
					//vm.planets = response[1].data.results
					console.log("PEOPLES", response[0])
					console.log("FILMS", response[1])
				})

                // var vm = this
                // var urlApi = 'https://swapi.co/api/people/'
                // this.axios.get(urlApi)
                //      .then(response => {
                //      	vm.peoples = response.data.results
					// 	 console.log(vm.peoples)
                //      }).catch(e => {
                //         console.log('Erro:', e)
            },
            // next() {
				// var l = this.getPeoples(this.peoples.next)
            //     console.log(l)
            // },
            // previous() {
				// this.getPeoples(this.api.previous)
            // }
        }
	}
</script>

<style scoped>

</style>