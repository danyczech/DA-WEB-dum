<template>
  <div id="app">
    <header>
      <h1>Chytrý dům</h1>
    </header>

    <main>
      <seznam :svetla="svetla" @zmena-mistnosti="nastavDetail($event)" />
      <!-- komponenta <seznam /> obsahuje seznam všech světel v domě. -->

      <detail :mistnost="svetla[mistnostDetail]" />
      <!-- komponenta <detail /> ovládá světlo ve vybrané místnosti domu  -->
    </main>
  </div>
</template>

<script lang="ts">
// import komponent ze složky components
import Seznam from "./components/Seznam.vue";
import Detail from "./components/Detail.vue";

export default {
  components: {
    // registrace naimportovaných komponent
    seznam: Seznam,
    detail: Detail,
  },

  data: function () {
    return {
      // v poli svetla je seznam světel
      // každé světlo má název a true/false hodnotu, zda je zapnuté nebo ne
      svetla: [
        {
          nazev: "Obývací pokoj",
          zapnuto: false,
        },
        {
          nazev: "Ložnice",
          zapnuto: true,
        },
        {
          nazev: "Dětský pokoj",
          zapnuto: false,
        },
        {
          nazev: "Koupelna",
          zapnuto: false,
        },
        {
          nazev: "Kuchyně",
          zapnuto: true,
        },
        {
          nazev: "Chodba",
          zapnuto: false,
        },
        {
          nazev: "Záchůdek",
          zapnuto: false,
        },
      ],

      mistnostDetail: 0, //počáteční nastavení místnosti v detailu
    };
  },

  methods: {
    //mění místnost v detailu při kliknutí na místnost v seznamu místností
    nastavDetail(index) {
      return (this.mistnostDetail = index);
    },
  },
};
</script>

<style></style>
