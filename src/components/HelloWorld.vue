<template>
<div >
<form @submit.prevent="addItem()">
  <div>
    <label>Vrsta:</label>
      <input type="text" v-model="animal.specie"  />
    <label>Ime:</label>
      <input type="text" v-model="animal.name" />
    <label>Rodjendan:</label>
      <input type="text" v-model="animal.birthday">
    <label>Sektor:</label>
  <select v-model="animal.sector">
    <option v-for="(sector) in sectors" :key="sector" :value="sector">{{sector}}</option>
    </select>
    </div>
      <button type="submit">add</button>
    </form>
    <table style="width:100%">
    <tr>
      <th>Vrsta</th>
      <th>Ime</th>
      <th>Datum</th>
      </tr>
    <tr v-for="(animal,index) in animals" :key="index"> 
      <td> {{animal.specie}}</td>
      <td> {{animal.name}}</td>
      <td> {{animal.birthday ? animal.birthday :'nepoznato'}}</td>
      <td> {{animal.sector}} </td>
        <button @click="removeItem(index)">Delete</button>
        <button @click="moveToTop(index)">MoveToTop</button>
    </tr>
    </table>
    <table style="width:100%">
    <tr>
      <th>Sector</th>
    </tr>
    <tr v-for="(sector,index) in sectors" :key="index"> 
      <td> {{sector}} </td>  
      <button @click="vidiZivotinju(sector)"> vidi zivotinju</button>
    </tr>
    </table>
</div>
</template>

<script>
export default {
  data() {
    return {
      animals: [
        {
          specie: "Tiger",
          name: "Nensy",
          birthday: "20.03.2010",
          sector: "opanse zivotinje"
        },
        {
          specie: "Bear",
          name: "Dundi",
          birthday: "23.082015",
          sector: "spavalice"
        },
        {
          specie: "Seagle",
          name: "Lord",
          birthday: "30.05.2013",
          sector: "ptice"
        },
        { specie: "Donky", 
          name: "Baba", 
          birthday: "", 
          sector: "domace" },
        {
          specie: "Octopod",
          name: "Sisy",
          birthday: "10.02.2018",
          sector: "vodene"
        }
      ],

        animal: {
          name: "",
          specie: "",
          birthday: "",
          sector: ""
        },

        sectors: ["opanse zivotinje", "spavalice", "ptice", "domace", "vodene"]
      };
  },

  methods: {

    removeItem(index) {
        this.$delete(this.animals, index);
    },
    moveToTop(index) {
      const animal = this.animals[index];
      this.animals.splice(index, 1);
      this.animals = [animal, ...this.animals];
    },

    addItem() {
      this.animals.push({ ...this.animal });
    },

    vidiZivotinju(sector) {

      let animalSector = this.animals.filter(animal => {return animal.sector === sector;});
      alert(JSON.stringify(animalSector));

      // var a = '';
      // for(var i=0;i<this.animals.length;i++){
      //   if(this.animals[i].sector === sector){
      //     a += this.animals[i].name;
      //   }
      // }
      // alert(a);
 
    }
  }
};
</script>

<style>
</style>
