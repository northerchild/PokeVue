<template>
	<default-layout>
		<section slot="filters" class="pokedex-filters mb-5">
			<div class="container">
				<div class="row">
					<div class="col-md-12 col-lg-6 ml-auto mr-auto">
						<div class="text-center">
							<label>Busca a tu pokemon favorito:</label>
							<input type="text" class="form-control" v-model="filter" placeholder="Introduce el nombre del pokemon">
							<small id="emailHelp" class="form-text text-muted">Busca a tú pokemon favorito escribiendo su nombre</small>
						</div>
					</div>
				</div>
			</div>
		</section>
		<section slot="content" class="pokedex-items">
			<div class="row">
				<div class="col-md-4 mb-3" v-for="(item,index) in filteredPokemon":key="index" @click.prevent="goToDetail(item)">
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
	import _ from 'lodash'
	export default{
		name:'HomeView',
		data(){
			return{
				pokemon:[],
				filter: ''
			}
		},
		created(){
			getPokemon().then(response =>{
				this.pokemon = response.data
			}).catch(err => console.log(err))		
		},
		computed:{
			filteredPokemon(){
				return(this.filter === '') ? this.pokemon : this.pokemon.filter(item => {
					return _.includes(item.name.toLowerCase(), this.filter)
				})
			}
		},
		methods:{
			goToDetail(pokemon){
				this.$router.push({
					params:{
						pokemonName: pokemon.slug
					},
					name: 'DetailPokemon'
				})
			}
		},
		components:{
			DefaultLayout,
			PokeCard
		}
	}
</script>
<style></style>