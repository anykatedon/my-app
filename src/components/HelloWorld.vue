<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-8">
        <div class="card mt-4">
          <div class="card-header">Vue Axios Post Demo App</div>
          <div class="card-body">
            <form @submit.prevent="formSubmit">
              <div class="form-group">
                <input type="text" class="form-control" v-model="name" placeholder="Name" />
              </div>
              <div class="form-group">
                <textarea class="form-control" v-model="description" placeholder="Description"></textarea>
              </div>
              <button class="btn btn-success btn-block">Submit</button>
            </form>
          </div>
          <div class="card-footer">
            <strong>Output:</strong>
            <pre>
              {{output}}
            </pre>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  mounted() {
    // eslint-disable-next-line
    console.log("Component mounted.");
  },
  data() {
    return {
      name: "",
      description: "",
      output: ""
    };
  },
  methods: {
    formSubmit() {
      let currentObj = this;
      this.axios
        .post("http://localhost:3000/employees/", {
          name: this.name,
          description: this.description
        })
        .then(function(response) {
          currentObj.output = response.data;
          currentObj.name = '';
          currentObj.description = '';
        })
        .catch(function(error) {
          currentObj.output = error;
        });
    }
  }
};
</script>