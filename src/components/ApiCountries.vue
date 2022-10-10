<template>
  <div>
    <input-search
      :pais="paisNombre"
      @update:pais="updatePais"
      :continente="continenteNombre"
      @update:continente="updateContinent"
    />
    <div class="grid">
      <card-countries v-for="(info, i) in filtrarContinente" :info="info" :key="i" />
    </div>
  </div>
</template>

<script>
import CardCountries from "./CardCountries.vue";
import InputSearch from "./InputSearch.vue";

export default {
  created() {
    fetch("https://restcountries.com/v3.1/all")
      .then((el) => el.json())
      /* .then(el => console.log(el)) */
      .then(
        (json) =>
          (this.informacion = json.map((el) => {
            return {
              //Para las cards
              nombreC: el.name.common,
              bandera: el.flags.png,
              poblacion: el.population,
              capital: el.capital,
              region: el.region,
              //Para las modals
              nombreO: el.name.official,
              subregion: el.subregion,
              dominio: el.tld,
              moneda: el.currencies,
              lenguajes: el.languages
              
            };
          }))
      );
  },
  name: "ApiCountries",

  data() {
    return {
      informacion: [],
      paisNombre: "",
      continenteNombre: "Todos",
    };
  },
  components: {
    CardCountries,
    InputSearch,
  },
  methods: {
    updatePais(pais) {
      this.paisNombre = pais;
    },
    updateContinent(continente) {
      this.continenteNombre = continente;
    },
  },
  computed: {
    filtrar: function () {
      return this.informacion.filter((pais) => {
        return pais.nombreC
          .toLocaleLowerCase()
          .includes(this.paisNombre.toLocaleLowerCase())
      });
    },
    filtrarContinente: function(){
      return this.filtrar.filter((pais) => {
        return this.continenteNombre.includes("Todos")
          ? pais
          : pais.region.includes(this.continenteNombre);
      })
    }
  },
};
</script>

<style>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, 400px);
  justify-content: center;
  align-items: center;
  width: 100vw;
}

@media screen and (max-width: 400px) {
  .grid{
    grid-template-columns: repeat(auto-fit, 375px);
  }
}
</style>
