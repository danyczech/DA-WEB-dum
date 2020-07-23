<template>
	<div class="detail">
		<div class="detail-inner">

			<div class="detail-ikona">
			<img :src="mistnost.zapnuto ? '/images/light-on.svg':'/images/light-off.svg'">
			<!-- zobrazuje správnou ikonu světla dle toho, zda je světlo v zobrazované místnosti zapnuto či vypnuto -->	
			</div>
						
			<h2 class="detail-nazev">
				{{mistnost.nazev}}
			</h2>

			<div class="detail-buttons">
				<button @click="rozniZhasni" 
				:class="{aktivni : mistnost.zapnuto === false}"> Zapnout </button>
				<button @click="rozniZhasni"
				:class="{aktivni : mistnost.zapnuto === true}"> Vypnout </button>
				<!-- při kliknutí na tlačítka Zapnout a Vypnout se zapíná a vypíná světlo pomocí funkce rozniZhasni -->
			</div>

		</div>
	</div>
</template>


<script>
export default {

	props: ['mistnost'], //přijímá z hlavní stránky jeden prvek z pole svetla - místnost, na kterou se kliklo a jejíž detail se zobrazí v této komponentě

	methods: {
		rozniZhasni () {
			this.mistnost.zapnuto = !this.mistnost.zapnuto;
		} // rožíná a zhasíná světlo 
	}
}
</script>

<style>

</style>