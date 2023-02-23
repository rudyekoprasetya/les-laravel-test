<template>
    <div class="tambah">
        <div class="container mt-3">
            <h1>Tambah Data</h1>
            <div class="row">
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
               
                <p><button class="btn btn-lg btn-success" @click="addData">Simpan</button>  <router-link class="btn btn-large btn-lg btn-warning" to="/">Batal</router-link></p>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
 
export default {
    name: 'TambahView',
    data() {
        return{
            date: null,
            todo: null,
            status: null
        }
    },
    methods: {
        addData(){
            let formData= new FormData();
            formData.append('date',this.date);
            formData.append('todo',this.todo);
            formData.append('status',this.status);
            //simpan data
            axios.post('http://localhost:8000/api/todo',formData)
            .then(res=>{
                console.log(res);
                //kembali ke home
                this.$router.push('/');
            })
        }
    }
}
</script>