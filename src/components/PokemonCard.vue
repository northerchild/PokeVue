<template>
	<div class="pokedex-card">
		<img :src="pokemon.ThumbnailImage" class="pokedex-card-img">
		<div class="pokedex-card-details">
			<small class="pokedex-card-details-title">#{{pokemon.number}}</small>
			<h4 class="poxedex-card-datails_title">{{pokemon.name}}</h4>
			<div class="pokedex-card_types">		
			</div>
		</div>
	</div>
</template>
<script>
	export default{
		name: 'PokeCard',
		props:{
			pokemon:{
				type:Object,
				required:true
			}
		}
	}
</script>