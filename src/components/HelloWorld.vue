<template>

<div>

  <form v-on:submit.prevent="addAnimal()">
  <label for="sort" >sort:  </label>
  <input v-model="animal.sort" type="text" name="sort" ><br>

  <label for="name">name:  </label>
  <input v-model="animal.name" type="text" name="name"><br>

  <label for="dateOfBirth"> Date Of Birth:  </label>
  <input v-model="animal.dateOfBirth" type="text" name="dateOfBirth"><br><br>

  <button type="submit"> add animal</button> 

    <label for="sektor">sektor  </label>
    <select v-model="animal.sektor">
      <option v-for="sektor in sektorList"  :key="sektor">
        {{sektor}}
      </option>

    </select>


  </form>
 <br>  <br> 

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
<td> {{animal.sektor ? animal.sektor : "Nepoznat"}} </td>
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
        }
      ],
    animal: {
      sort: "",
      name: "",
      dateOfBirth: "",
      sektor: ""
    },
    sektorList: ['ptice', 'gmizavci', 'sisari', 'insekti']

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
    },
    addAnimal(animal){
      this.animalList.push({...this.animal});
    }
  }

}
</script>

<style>

</style>
