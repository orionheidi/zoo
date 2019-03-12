<template>
  <table style="width:100%">
  <tr>
    <th>Vrsta</th>
    <th>Ime</th>
    <th>Datum</th>
   </tr>
  <tr  v-for="(animal,index) in animals" :key="animal"> 
     <td> {{animal.specie}}  {{ index }}</td>
    <td> {{animal.name}}   {{ index }}</td>
     <td> {{animal.birthday ? animal.birthday :'nepoznato'}}   {{ index }}</td>
    <button @click="removeItem(index)">Delete</button>
  </tr>
</table>
</template>

<script>
export default {
  data () {
       return{
        animals: [
          {specie:"Tiger", name:"Nensy", birthday:"20.03.2010"},
          {specie:"Bear", name:"Dundi", birthday:"23.082015"},
          {specie:"Seagle", name:"Lord", birthday:"30.05.2013"},
          {specie:"Donky", name:"Baba", birthday:""},
          {specie:"Octopod", name:"Sisy", birthday:"10.02.2018"},

        ]
       
       }
   },

    methods: {

     removeItem(index) {
      if (this.deleteWithSplice) {
        this.animals.splice(index, 1);
      } else {
        this.$delete(this.animals, index);
      }
    },
   }

}
</script>

<style>

</style>
