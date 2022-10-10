<template>
  <div class="inputFlex">
    <input
      type="text"
      class="input"
      placeholder="Ingresa el nombre de algun pais"
      :value="pais"
      @input="(event) => $emit('update:pais', event.target.value)"
    />

    <select
      :name="continente"
      :value="continente"
      @change="(event) => $emit('update:continente', event.target.value)"
      class="select"
    >
      <option>Todos</option>
      <option>Europe</option>
      <option>Asia</option>
      <option>Americas</option>
      <option>Africa</option>
      <option>Antarctic</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "InputSearch",
  props: ["pais", "continente"],
};
</script>

<style>
.inputFlex {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.select {
  width: 180px;
  height: 35px;
  margin-top: 40px;
  margin-left: 10px;
  border-radius: 8px;
  border: 1px solid rgba(0, 0, 0, 0.241);
}

.input {
  margin-top: 40px;
  height: 35px;
  width: 400px;
  text-align: center;
  border-radius: 8px;
  border: 1px solid rgba(0, 0, 0, 0.241);
}

@media screen and (max-width: 1000px){
  .input{
    width: 250px;
  }
  .select{
    width: 120px;
  }
}
</style>
