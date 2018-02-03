<script>
	import DefaultLayout from '@/layout/DefaultLayout' //eslint-disable-line no-unused-vars
	import PokeCard from '@/components/PokemonCard'
	export default{
		name:'DetailPokemonView',
		render(h){
		let pokemon = this.$route.params.pokemon		
		if (!pokemon) {
			this.$router.push({ name: 'Home' })
		}else{
		return <DefaultLayout>
				<section slot="content" class="pokedex-item mt-5">
					<div className="row">
						<div class="col-md-12">
						 <h1 class="pokemon-datail_tittle text-center mb-5">{pokemon.name}
						 	<span class="text-muted">#{pokemon.number}</span>
						 </h1>
						 <hr />
						 <div className="row">
						 	<div className="col-md-5">
						 		<img class="pokedex-detalle" src={pokemon.ThumbnailImage}/>
						 	</div>
						 </div>
						</div>
					</div>
				</section>
			</DefaultLayout>					
		}
		}
	}
</script>
<style></style>