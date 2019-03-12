<template>
  <table style="width:100%">
  <tr>
    <th>Vrsta</th>
    <th>Ime</th>
    <th>Datum</th>
  </tr>
  <tr>
    <td v-for="(animal) in animals" :key="animal">
      {{animal}} 
    </td>
  </tr>
    </tr>
</table>
</template>

<script>
export default {
  data () {
       return{
        animals: {
          specie:"Tiger", name:"Nensy", birthday:"20.03.2010",
          specie:"Bear", name:"Dundi", birthday:"23.082015",
          specie:"Seagle", name:"Lord", birthday:"30.05.2013",
          specie:"Donky", name:"Baba", birthday:"15.04.2012",
          specie:"Octopod", name:"Sisy", birthday:"10.02.2018",

        }
       
       }
   },

}
</script>

<style>

</style>
