<template>
  <div>
    <div class="card" @click="aside = !aside">
      <img :src="info.bandera" :alt="info.nombreC" />
      <div class="texto">
        <h3 class="titulo">{{ info.nombreC }}</h3>

        <p v-if="info.capital !== undefined">
          <b>Capital:</b> {{ info.capital[0] }}
        </p>
        <p><b>Region:</b> {{ info.region }}</p>
        <p><b>Poblacion:</b> {{ info.poblacion }}</p>
      </div>
    </div>
    <section class="modal" v-if="aside">
      <p class="close white" @click="aside = !aside">&times;</p>

      <img :src="info.bandera" class="bandera" :alt="info.nombreC" />
      <div class="modalGrid">
        <h2 class="title">{{ info.nombreC }}</h2>
        <p>
          <b>Nombre oficial:</b><i class="p"> {{ info.nombreO }}</i>
        </p>
        <p>
          <b>Poblacion:</b> <i class="p">{{ info.poblacion }}</i>
        </p>
        <p>
          <b>Region:</b> <i class="p">{{ info.region }}</i>
        </p>
        <p>
          <b>Sub Region:</b> <i class="p">{{ info.subregion }}</i>
        </p>
        <p v-if="info.capital !== undefined">
          <b>Capital:</b> <i class="p">{{ info.capital[0] }}</i>
        </p>
        <p>
          <b>Dominio:</b> <i class="p">{{ info.dominio[0] }}</i>
        </p>
        <p>
          <b>Moneda:</b>
          <i class="p"
            > {{ info.moneda | mostrarMoneda }} ({{
              info.moneda | mostrarAbreviacionMoneda
            }})</i
          >
        </p>
        <p>
          <b>Lenguaje:</b> <i class="p">{{ info.lenguajes | mostrarIdioma }}</i>
        </p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "CardCountries",
  props: ["info"],
  data() {
    return {
      aside: false,
    };
  },
  filters: {
    mostrarMoneda: function (objeto) {
      for (const nombre in objeto) {
        return objeto[nombre].name;
      }
    },
    mostrarAbreviacionMoneda: function (objeto) {
      for (const nombre in objeto) {
        return nombre;
      }
    },
    mostrarIdioma: function (objeto) {
      let result = "";
      for (const nombre in objeto) {
        result = `${result}, ${objeto[nombre]}`;
      }
      let string = result.slice(1);
      return string;
    },
  },
};
</script>

<style scoped>
.title {
  margin-bottom: 15px;
}
.modal {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgb(255, 255, 255);
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  z-index: 100;
}
.card {
  border: 1px solid rgba(83, 83, 83, 0.077);
  height: 380px;
  border-radius: 16px;
  display: grid;
  justify-content: center;
  width: 300px;
  text-align: center;
  background: rgb(254, 254, 254);
  box-shadow: 0px 0px 10px 3px rgba(34, 34, 34, 0.07);
  margin: 40px;
  cursor: pointer;
}

.modalGrid {
  text-align: justify;
}

.p {
  color: grey;
}

.bandera {
  box-shadow: 0px 0px 10px 10px rgba(34, 34, 34, 0.059);
  min-height: 300px;
  max-width: 700px;
}

.texto {
  text-align: left;
  margin-left: 30px;
}

.titulo {
  margin-bottom: 5px;
}

.close {
  cursor: pointer;
  position: fixed;
  top: 0;
  right: 0;
  transform: translateX(-50%);
  font-size: 50px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -khtml-user-select: none;
  -ms-user-select: none;
  z-index: 100;
}

.card img {
  width: 300px;
  height: 200px;
  text-align: center;
  border-top-right-radius: 16px;
  border-top-left-radius: 16px;
}

@media screen and (max-width: 1000px){

  .modal{
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }
  .bandera{
    width: 300px;
    min-height: 30px;
    margin-top: 20px;
  }
  .p {
  margin-left: 0px;
  padding: 5px;
}
.modalGrid{
  padding: 20px;
}
}
</style>
