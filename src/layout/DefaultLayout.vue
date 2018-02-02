<template>
	<div class="default-layout">
		<!--Header-->
		<header-partial></header-partial>
		<!--End Header-->
		<!--Main-->
		<main class="main-section mb-5">
			<div class="container">
				<slot name="content"></slot>
			</div>
		</main>
		<!--End Main-->
		<!--Footer-->
		<footer-partial></footer-partial>
		<!--End Footer-->
	</div>
</template>
<script>
	import HeaderPartial from '@/partials/HeaderPartial'
	import FooterPartial from '@/partials/FooterPartial'
	export default{
		name: 'DefaulLayout',
		components:{
			HeaderPartial,
			FooterPartial
		}
	}
</script>
