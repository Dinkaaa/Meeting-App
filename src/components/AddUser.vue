<template>
  <div class="AddUser col-6">
      <div class="input-block form-group">
          <span>Name</span>
          <input class="form-control" type="text" v-model="name">
      </div>
      <div class="input-block form-group">
          <span>Surname</span>
          <input class="form-control" type="text" v-model="surname">
      </div>
      <button class="btn btn-info" @click="addUser()">Add</button>
  </div>
</template>
<script>

import DataService from '.././dataService'
export default {
  data(){
      return{
          name: '',
          surname: ''
      }
  },
  methods: {
    addUser() {
        if(this.name && this.surname){
             this.$store.commit('ADD_USER', {userName: this.name + ' ' + this.surname});
             DataService.sendData(this.$store, 'users');
             this.name='';
             this.surname='';
        }
           
    }
  }
}
</script>

