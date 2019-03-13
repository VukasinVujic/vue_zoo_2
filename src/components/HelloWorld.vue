<template>

<div>
<table>

<tr>
  <th> Sort </th>
  <th> Name </th>
  <th> Date of birth  </th>
  <th>Removing items</th>
</tr>

<tr v-for="(animal,index) in animalList" :key="animal.name">

<td> {{animal.sort}} </td>
<td> {{animal.name}} </td>
<td> {{animal.dateOfBirth ? animal.dateOfBirth : "Nepoznat"}} </td>
<td> <button @click="removeItem(index)"> remove </button></td>
<td> <button @click="moveToTheTop(index)"> to the top </button></td>

</tr>

</table>
</div>



  
</template>

<script>
export default {
  data(){
    return {
      animalList: [
        {
          sort: "pas",
          name: "lepi",
          dateOfBirth: "12.02.2000"
        },
        {
          sort: "macka",
          name: "figaro",
          dateOfBirth: "12.02.2005"
        },
        {
          sort: "papagaj",
          name: "ubica",
          dateOfBirth: "12.02.2010"
        },
        {
          sort: "guster",
          name: "mekani",
          dateOfBirth: ""
        },
        {
          sort: "slon",
          name: "malecki",
          dateOfBirth: "12.02.2007"
        },
      ]
    };
  },
  methods: {
    removeItem(index){
      this.animalList.splice(index,1);
    },
    moveToTheTop(index){
      let aaa = this.animalList[index];
      this.animalList.splice(index,1);
      this.animalList.unshift(aaa);
    }
  }

}
</script>

<style>

</style>
