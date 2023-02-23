<template>
    <div class="edit">
        <div class="container mt-3">
            <h1>Edit Data</h1>
            <div class="row">
                <div class="mb-3">
                    <label for="id" class="form-label">ID</label>
                    <input type="text" class="form-control" v-model="id" readonly>
                </div>
                <div class="mb-3">
                    <label for="nama" class="form-label">Date</label>
                    <input type="date" class="form-control" v-model="date">
                </div>
                <div class="mb-3">
                    <label for="alamat" class="form-label">Todo</label>
                    <textarea class="form-control" rows="3" v-model="todo"></textarea>
                </div>
                <div class="mb-3">
                    <label for="gender" class="form-label">Status</label>
                    <select class="form-control" v-model="status">
                        <option value="Y">Y</option>
                        <option value="N">N</option>
                    </select>
                </div>
               
                <p><button class="btn btn-lg btn-success" @click="updateData">Update</button>  <router-link class="btn btn-large btn-lg btn-warning" to="/">Batal</router-link></p>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
 
export default {
    name: 'EditView',
    props: {
        dataTodos: []
    },
    data() {
        //tampilkan data di form
        return{
            id: this.dataTodos.id,
            date: this.dataTodos.date,
            todo: this.dataTodos.todo,
            status: this.dataTodos.status
        }
    },
    methods: {
        updateData(){
            let formData= new FormData();
            formData.append('id',this.id);
            formData.append('date',this.date);
            formData.append('todo',this.todo);
            formData.append('status',this.status);
            //ubah data
            axios.put('http://localhost:8000/api/todo',formData)
            .then(res=>{
                console.log(res);
                //kembali ke home
                this.$router.push('/');
            })
        }
    }
}
</script>