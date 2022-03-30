<template>
  <div>
    <center>
      <h1> Calcul de votre IMC...</h1>
    </center>
    <br />
    <div class="d-flex flex-column align-items-center">
      <form @submit.prevent="calcul_Imc">
        <div>
          <label for="taille"> Indiquer votre taille (cm) : </label>

          <input
            type="number"
            name="taille"
            id="taille"
            placeholder="en cm"
            min="130"
            max="220"
            v-model="imc.taille"
          />
        </div>
        <br />
        <div class="input-group">
          <label for="poids"> Indiquer votre poids (kg) : </label>

          <input
            type="number"
            name="poids"
            id="poids"
            placeholder="en kg"
            min="40"
            max="200"
            v-model="imc.poids"
          />
        </div>
        <br />
        <br />
        <center><span class="material-icons"> flaky </span>
          <input type="submit" value="Ready or not, here I come! 😱" /><span class="material-icons"> flaky </span>
        </center>
        <br /><br />
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
//pour rendre "reactif"imc
import { reactive } from "vue";
//pour garder les donées entrées dans le store et les réutiliser dans le tableau
import { useImcStore } from "../stores/imc";
//données réactives qui vont prendre les valeurs des champs inputs
const imc = reactive({
  taille: 0,
  poids: 0,
});
//store
const store = useImcStore();
//fonction permettant le calcul de l'imc
function calcul_Imc() {
  //calcul de l'IMC
  let calculateImc = Math.round((imc.poids / Math.pow(imc.taille, 2)) * 10000);
  //les données qui font references Aux chAmps inputs qui sont envoyées dans le store pour réutilisation dont la donnée d el'imc que l'on retrouvera dans le tableau recap
  store.imc = calculateImc;
  store.taille = imc.taille;
  store.poids = imc.poids;
}
</script>

<style>
label {
  display: block;
  width: 200px;
  float: left;
}

</style>