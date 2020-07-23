<template>
	<div class="svetla"> 
				
		<!-- Seznam místností v domě s ikonou světla, která je buď rozsvícená nebo zhasnutá -->
				
		<div v-for="(mistnost, index) in svetla"
           :key="index"
		   class="svetlo"
		   @click="zmenMistnost(index)"> 
			<!-- pokud se klikne na místnost v seznamu, emituje se přes funkci zmenMistnost index místnosti, na kterou se kliklo, do hlavní stránky -->
									
			<div class="svetlo-ikona">
			<img :src="mistnost.zapnuto ? '/images/light-on.svg':'/images/light-off.svg'">
			<!-- zjišťuje, zda je světlo rozsvíceno/zhasnuto a podle toho zobrazuje správnou ikonu světla -->	
			</div>
			
			<div class= "svetlo-nazev">
				{{mistnost.nazev}}
			</div>
		</div>

	</div>
</template>



<script>
export default {

	props: ['svetla'], //pole svetla z hlavní stránky

	methods: {
		zmenMistnost (index) {
			this.$emit ('zmena-mistnosti', index);
		}
		// emituje index místnosti, na kterou se kliklo, do hlavní stránky
	}
}
</script>

<style>

</style>