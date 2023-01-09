<template>
  <div id="app">
    <header>
      <h1>Chytrý dům</h1>
    </header>

    <main>
      <seznam :lights="lights" @zmena-mistnosti="setDetail($event)" />
      <!-- komponenta <seznam /> obsahuje seznam všech světel v domě. -->

      <detail :mistnost="lights[roomDetail]" />
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
      lights: [
        {
          roomName: "Obývací pokoj",
          switchOn: false,
        },
        {
          roomName: "Ložnice",
          switchOn: true,
        },
        {
          roomName: "Dětský pokoj",
          switchOn: false,
        },
        {
          roomName: "Koupelna",
          switchOn: false,
        },
        {
          roomName: "Kuchyně",
          switchOn: true,
        },
        {
          roomName: "Chodba",
          switchOn: false,
        },
        {
          roomName: "Záchůdek",
          switchOn: false,
        },
      ],

      roomDetail: 0, //starting value - room in detail
    };
  },

  methods: {
    //mění místnost v detailu při kliknutí na místnost v seznamu místností
    setDetail(index) {
      return (this.roomDetail = index);
    },
  },
};
</script>

<style></style>
