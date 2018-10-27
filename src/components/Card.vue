<template>
      <div>
         <div>
            {{ character.name}}
            {{ character.height }}cm
            {{ character.mass}}kg
            {{ character.hair_color}}
            {{ character.eye_color}}
         </div>
   </div>
</template>

<script>
	export default {
		props: ['id'],
		data () {
			return {
				character: {}
			}
		},
		methods: {
			fetchCharacter (id) {
				fetch (`https://swapi.co/api/people/${id}`, {
					method: 'GET',
				})
					.then(response => response.json())
					.then(json=> this.character = json)
			},
		},
		created () {
			this.fetchCharacter(this.id)
		}
	}
</script>