<template>
  <!-- <div class="col-md-3"></div> -->
  <div>
    <div class="col-md-3 col-sm-3"></div>
    <div class="col-md-6 col-sm-6 col-xs-12">
      <h1 class="text-danger text-center">Sign Up</h1>
      <form v-on:submit.prevent="addUser">
        <div class="row">
          <div class="col-md-5 col-sm-5">
            <div class="row">
              <div>
                <div class="form-group has-error has-feedback">
                  <label>Your Name:</label>
                  <input type="text" placeholder="user name" class="form-control input-sm" v-model="user.name">
                </div>
              </div>
            </div>
            <div class="row">
              <div>
                <div class="form-group has-error has-feedback">
                  <label>Your Email:</label>
                  <input type="text" placeholder="user@edit.com" class="form-control input-sm" v-model="user.email">
                </div>
              </div>
            </div>        
            <div class="row">
              <div>
                <div class="form-group has-error has-feedback">
                  <label>Birthday:</label>
                  <input type="date" class="form-control input-sm" style="padding-right: 10px" data-date-end-date='0d' v-model="user.birth">
                </div>
              </div>
            </div>
            <div class="row">
              <div>
                <div class="form-group has-error has-feedback">
                  <label>Sex: </label>
                  <input type="radio" v-model="user.sex" name="gender" value="M" checked> Male
                  <input type="radio" v-model="user.sex" name="gender" value="W"> Female
                </div>
              </div>
            </div>
          </div>
          <div class="col-md-2 col-sm-2"></div>
          <div class="col-md-5 col-sm-5">
            <div class="row">
              <div>
                <div class="form-group has-error has-feedback">
                  <label>Company:</label>
                  <input type="text" placeholder="company name" class="form-control input-sm" v-model="user.company">
                </div>
              </div>
            </div>
            <div class="row">
              <div>
                <div class="form-group has-error has-feedback">
                  <label>Telephone:</label>
                  <input type="text" placeholder="1234567890" class="form-control input-sm" v-model="user.telephone">
                </div>
              </div>
            </div>
            <div class="row">
                <div class="form-group has-feedback d-flex flex-row checkbox">              
                  <label class=""><input type="checkbox" class="form-check-input" v-model="user.visit"> Official Visit</label>
                  <label class=""><input type="checkbox" class="form-check-input" v-model="user.esc"> Escort Required</label>
                </div>
            </div>
            <div class="row" v-if=" user.esc == true ">
              <div >
                <div class="form-group has-error has-feedback">
                  <label>Escort Name:</label>
                  <input type="text" placeholder="name" class="form-control input-sm" v-model="user.esc_name">  
                </div>
              </div>
            </div>
            <div class="row">
              <div class="form-group">
                <button class="btn btn-danger">signup</button>
              </div>
            </div>  
          </div>
        </div>        
              
      </form>
    </div>
    <div class="col-md-3 col-sm-3"></div>
  </div>
  <!-- <div class="col-md-3"></div> -->
</template>
<script>
  export default {
    data(){
        return{
          user:{
            name: '',
            sex: 'M',
            birth: '04-05-1988',
            email: '',
            telephone: '',
            company: '',
            visit: false,
            esc: false,
            esc_name: ''
          }
        }
    },
    methods: {
      addUser(){
        let uri = 'http://localhost:4000/users/add';        
        this.axios.post(uri, this.user).then((response) => {
          this.$router.push({name: 'CreateUser'})
        });
        this.user = {};
      }
    }
  }
</script>
