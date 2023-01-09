<template>
  <div class="svetla">
    <!-- Seznam místností v domě s ikonou světla, která je buď rozsvícená nebo zhasnutá -->

    <div
      v-for="(room, index) in lights"
      :key="index"
      class="svetlo"
      @click="changeRoom(index)"
    >
      <!-- pokud se klikne na místnost v seznamu, emituje se přes funkci zmenMistnost index místnosti, na kterou se kliklo, do hlavní stránky -->

      <div class="svetlo-ikona">
        <img
          :src="
            room.switchOn ? '/images/light-on.svg' : '/images/light-off.svg'
          "
        />
        <!-- zjišťuje, zda je světlo rozsvíceno/zhasnuto a podle toho zobrazuje správnou ikonu světla -->
      </div>

      <div class="svetlo-nazev">
        {{ room.roomName }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["lights"], //pole svetla z hlavní stránky

  methods: {
    changeRoom(index) {
      this.$emit("zmena-mistnosti", index);
    },
    // emituje index místnosti, na kterou se kliklo, do hlavní stránky
  },
};
</script>

<style></style>
