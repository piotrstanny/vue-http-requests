<template>
  <div id="app">
  <div class="container">
      <div class="row justify-content-center">
        <div class="col-xs-12 col-md-6">
          <h1>A Form to connect with Firebase</h1>
          <form>
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
              <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
              <label for="exampleInputPassword1">Password</label>
              <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
            </div>
            <div class="form-group form-check">
              <input type="checkbox" class="form-check-input" id="exampleCheck1">
              <label class="form-check-label" for="exampleCheck1">Check me out</label>
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
        </div>
      </div>
  </div>
  </div>
</template>

<script>

export default {
  name: 'App',
}
</script>

<style>
.container{
  
}
h1 {
  text-align: center;
  height: 200px;
  padding-top:40px;
}
</style>