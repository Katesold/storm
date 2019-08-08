<template>
    <div class="tableCont">
        <h2>Employees</h2>      
        <table>
        <thead class="tableHeads">
          <tr>
            <th class="mainTH">Identifier</th>
            <th class="mainTH">Name</th>
            <th class="mainTH">Email</th>
            <th class="mainTH">Date</th>
            <th class="mainTH">Departments</th>
            <th class="mainTH">Status</th>
          </tr>
        </thead>
          <tr class ="row" v-bind:key="employee.id" v-for="(employee) in json">
              <td> {{employee.identifier}} </td>
              <td> {{employee.first_Name}} {{employee.last_Name}}  </td>
              <td> {{employee.email}} </td>
              <td> {{employee.createdDate}} </td>
              <td v-bind:key="index" v-for="(department, index) in employee.employeeDepartments"> <span v-bind:key="index" v-for="(dep, index) in department"> {{ dep.description }}   </span> </td>
          </tr>
          
      </table>
    </div>
</template>

<script>
import json from '.././assets/employees.json'
export default {
    data() {
    return {
      json: json.results
    }
  },
}
</script>

<style scoped>
.tableCont{
    padding-top: 20px;
}
h2{
    padding: 20px;
    font-size: 2em;
}
table{
    padding: 10px;
    border-collapse: collapse;
}
td{
    padding: 10px;
    border-bottom: 1px solid #FFF;
}
th{
    padding-left: 10px;
}

table, tr {
  border: 1px solid #FFF;
  text-align: left;
}
</style>