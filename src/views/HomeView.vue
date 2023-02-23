<template>
  <div class="home">
    <div class="container mt-3">
      <div class="row">
        <div class="col">
          <h1>Todo Apps</h1>
          <router-link class="btn btn-success btn-small" to="/tambah">Tambah Data</router-link>
          <div class="table-responsive">
            <table class="table">
              <thead>
                <tr>
                  <th scope="col">#</th>
                  <th scope="col">Date</th>
                  <th scope="col">Todo</th>
                  <th scope="col">Status</th>
                  <th scope="col">Aksi</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in todos" :key="item.id">
                  <th scope="row">{{item.id}}</th>
                  <td>{{item.date}}</td>
                  <td>{{item.todo}}</td>
                  <td>{{item.status}}</td>
                  <td>
                    <!-- edit button  -->
                    <router-link class="btn btn-small btn-warning" :to="{name: 'Edit', params: { dataTodos : item } }">Edit</router-link> | <!-- hapus button  -->
                    <button class="btn btn-small btn-danger" @click="delData(item.id)">Hapus</button>
                  </td>
                </tr>
              </tbody>
            </table>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
 
export default {
  name: 'HomeView',
  data() {
    return {
      todos:{}
    }
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData(){
      axios.get('http://localhost:8000/api/todo')
      .then(
        res=>{
          console.log(res.data.data);
          this.todos=res.data.data;
        }
      )
    },
    delData() {
      axios.delete('http://localhost:8000/api/todo')
      .then(
        res=>{
          console.log(res);
          //reload data
          this.getData();
        }
      )
    }
  }
}
</script>
