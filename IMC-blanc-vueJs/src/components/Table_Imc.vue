  
<template>
  <center>
    <br />

    <div class="card" style="">
      <br />

      <table class="table">
        <tr>
          <th scope="col">
            Taille(cm) <span class="material-icons"> straighten </span>
          </th>
          <th scope="col">
            Poids(kg) <span class="material-icons"> scale </span>
          </th>
          <th scope="col">
            IMC <span class="material-icons"> equalizer </span>
          </th>
        </tr>

        <tbody>
          <tr>
            <td class="table-active">{{ store.taille }}</td>
            <td class="table-active">{{ store.poids }} kg</td>
            <td>{{ store.imc }}</td>
          </tr>
        </tbody>
      </table>
      <br />
    </div>
  </center>
  <br />

</template>















<script setup lang="ts">
//pour pouvoir utiliser les données du store il faut déjà un import
import { useImcStore } from "@/stores/imc";
//et ne pas oublierle const
const store = useImcStore();
</script>


<style>
table {
  margin: 10px;
}
table,
th,
td {
  border: 1px solid;
}
td,
tr {
  width: 600px;
  padding: 20px;
}
</style>