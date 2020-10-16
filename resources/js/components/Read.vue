<template>

  <div>
    <!-- disini saya menggunakan bootstrap untuk design tabel nya. secara default bootstrap sudah di include di file welcome.blade.php jadi saya tidak perlu lagi untuk import file nya -->
    <div class="row">
      <div class="col-md-12">
        <div class="row">
          <div class="col-md-10" style="text-align:center">
            <a class="btn btn-lg disabled btn-default">Data User</a>
          </div>
          <div class="col-md-2">
            <!-- push router ke form membuat data -->
              <router-link class="btn btn-primary w-100" to="/create">+ Tambah User</router-link>
          </div>
        </div>
        <br>
        <table class="table">
          <thead>
            <tr>
              <th scope="col">username</th>
              <th scope="col">email</th>
              <th scope="col">Action</th>
            </tr>
          </thead>
          <tbody>
            <!-- menampilkan data ke table -->
            <tr v-for="person in persons" :key="person.id">
              <td style="width:40%">{{person.first_name}}</td>
              <td style="width:40%">{{person.last_name}}</td>
              <td style="width:20%">
                <router-link class="btn btn-sm btn-warning" :to="'/detail/'+person.id">Update</router-link>
                <button class="btn btn-sm btn-danger" v-on:click="deleteData(person.id)">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<!-- script js -->
<script>
export default {
  data() {
    return {
      // variable array yang akan menampung hasil fetch dari api
      persons: []
    };
  },
  created() {
    this.loadData();
  },
  methods: {
    loadData() {
      // fetch data dari api menggunakan axios
      axios.get("http://localhost:8000/api/user/person")
      .then(response => {
        // mengirim data hasil fetch ke varibale array persons
        this.persons = response.data;
        
      });
    },
    deleteData(id) {
      // delete data
      axios.delete("http://localhost:8000/api/user/person/" + id).then(response => {
        this.loadData();
      });
    }
  }
};
</script>