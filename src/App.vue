<template>
  <div id="app">
  <div class="container">
      <div class="row justify-content-center">
        <div class="col-xs-12 col-md-6">
          <h1>A Form to connect with Firebase</h1>
          <form>
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email" v-model="user.email">
              <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
              <label for="nickname">Nickname</label>
              <input type="text" class="form-control" id="nickname" placeholder="Enter nickname" v-model="user.nickname">
            </div>
            <div class="form-group form-check">
              <input type="checkbox" class="form-check-input" id="exampleCheck1">
              <label class="form-check-label" for="exampleCheck1">Check me out</label>
            </div>
            <button type="submit" class="btn btn-primary" @click.prevent="submit">Submit</button>
          </form>
        </div>
      </div>
  </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      user: {
        email: '',
        nickname: ''
      }
    }
  },
  methods: {
    submit() {
      return console.log("Nickname is " + this.user.nickname + ", and email is " + this.user.email)
    }
  }
}
</script>

<style>
h1 {
  text-align: center;
  height: 200px;
  padding-top:40px;
}
</style>