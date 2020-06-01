<template>
  <div id="app">
    <label >Choose a Category:</label>
    <select v-model="category">
      <option value="Book">Books</option>
      <option value="Magazine">Magazines</option>
      <option value="Newspaper">Newspapers</option>
      <option value="Others">Others</option>
      <option value="All">All</option>
    </select>
    <table id="table" border = "1" >
      <thead>
        <tr>
          <th>Code</th>
          <th>Name</th>
          <th>Description</th>
          <th>Category</th>
        </tr>
      </thead>
      <tbody>
        <tr :key="item.code" v-for="item in filteredList">
          <td>{{ item.code }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.description }}</td>
          <td>{{ item.category }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
//import data from "./data.json";
import * as data from "./data2.json";

export default {
  name: 'App',
  components: {
  },

  data(){
    return{
      category:"",
      //list: data
      list: data.obj
      /*list: [
        {
          code: "1",
          name: "Lord of the Rings",
          description: "JRR Tolkien",
          category: "Book"
        },
        {
          code: "2",
          name: "FORBS",
          description: "Millionairies in the world",
          category: "Magazine"
        },
        {
          code: "3",
          name: "Los Tiempos",
          description: "Clasificados",
          category: "Newspaper"
        },
        {
          code: "4",
          name: "Lagartija",
          description: "Book of jokes",
          category: "Others"
        }
      ]*/
    }
    
  },

  computed: {
    filteredList() {
      return this.category === "" || this.category === "All"
        ? this.list
        : this.list.filter(item => item.category === this.category);
    }
  },

  
}
</script>

<style>
table {
  font-family: 'Open Sans', sans-serif;
  width: 750px;
  border-collapse: collapse;
  border: 3px solid #44475C;
  margin: 10px 10px 0 10px;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475C;
  color: #FFF;
  padding: 8px;
  min-width: 30px;
}

table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7D82A8;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #D4D8F9;
}

</style>
