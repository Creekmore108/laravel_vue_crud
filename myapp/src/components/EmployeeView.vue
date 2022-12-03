<template>
  <div>
    <h2>Employee View</h2>
    <table class="table table-dark">
  <thead>
    <tr>
      <th scope="col">Id</th>
      <th scope="col">Employee Name</th>
      <th scope="col">Address</th>
      <th scope="col">Mobile</th>
    </tr>
    </thead>
    <tbody>
        <tr v-for="task in result" v-bin:key="task.id">
        <th scope="row">1</th>
        <td>{{ task.id }}</td>
        <td>{{ task.name }}</td>
        <td>{{ task.address }}</td>
        <td>{{ task.mobile }}</td>
        </tr>
        
    </tbody>
    </table>
   
  </div>
</template>

<script>

import Vue from 'vue';
import axios from 'axios';

Vue.use(axios)

export default {
  name: 'EmployeeView',
  data () {
        return {
            result: {}
        }
    },
    created() {
        this.EmployeeLoad();
    },

    methods: {
        EmployeeLoad(){
            var page = "http://laravel_vue_crud.test/api/employees";
            axios.get(page)
                .then(
                    ({data})=>{
                        console.log(data);
                        this.result = data;
                    }
                );
        }
    }
}
</script>