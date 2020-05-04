<template>
  <div id="app">
  <div class="container">
      <div class="row justify-content-center">
          <h1>A Form to connect with Firebase</h1>

        <div class="col-xs-12 col-md-6">
          <h2>Send data to database</h2>
          <form>
            <div class="form-group">
              <label for="exampleInputEmail1">Email address</label>
              <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email" v-model="user.email">
              <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
              <label for="nickname">Username</label>
              <input type="text" class="form-control" id="nickname" placeholder="Enter nickname" v-model="user.nickname">
            </div>
            <button class="btn btn-primary" @click.prevent="submit">Submit</button>
          </form>
        </div>

        <div class="col-xs-12 col-md-6">
          <h2>Get data from database</h2>
          <label for="">Choose access node:</label>
          <input class="form-control" type="text" v-model="node">
          <br>
          <button class="btn btn-warning" @click="fetchData">Get Data</button>
          <div id="data-list">
            <ul class="list-group">
              <li class="list-group-item" v-for="u in users" :key="u">{{u.nickname}} - {{u.email}}</li>
            </ul>
          </div>
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
      },
      users: [],
      resource: {},
      node: 'data'
    }
  },
  methods: {
    submit() {
      this.$http.post('', this.user)
        .then(response => {
          return console.log(response)
        }, error => {
          return console.log(error)
        });
        this.resource.save({}, this.user);
        this.resource.saveAlt(this.user)
    },
    fetchData() {
//                this.$http.get('data.json')
//                        .then(response => {
//                            return response.json();
//                        })
//                        .then(data => {
//                            const resultArray = [];
//                            for (let key in data) {
//                                resultArray.push(data[key]);
//                            }
//                            this.users = resultArray;
//                        });
        this.resource.getData({node: this.node})
                .then(response => {
                    return response.json();
                })
                .then(data => {
                    const resultArray = [];
                    for (let key in data) {
                        resultArray.push(data[key]);
                    }
                    this.users = resultArray;
                })
    },
    created() {
        const customActions = {
            saveAlt: {method: 'POST', url: 'alternative.json'},
            getData: {method: 'GET'}
        };
        this.resource = this.$resource('{node}.json', {}, customActions);
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
h2 {
  margin-bottom: 50px;
}
#data-list {
  margin-top: 30px;
}
</style>