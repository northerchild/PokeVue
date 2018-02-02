<template>
	<default-layout>
		<section slot="content" class="pokedex-items">
			<div class="row">
				<div class="col-md-4" v-for="(item,index) in pokemon":key="index">
					<poke-card :pokemon='item'></poke-card>
				</div>
			</div>
		</section>	
	</default-layout>
</template>
<script>
	import DefaultLayout from '@/layout/DefaultLayout'
	import {getPokemon} from '@/service/pokemon'
	import PokeCard from '@/components/PokemonCard'
	export default{
		name:'HomeView',
		data(){
			return{
				pokemon:[]
			}
		},
		created(){
			getPokemon().then(response =>{
				this.pokemon = response.data
			}).catch(err => console.log(err))		
		},
		components:{
			DefaultLayout,
			PokeCard
		}
	}
</script>
<style></style>