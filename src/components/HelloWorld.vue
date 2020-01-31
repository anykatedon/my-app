<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-8">
        <div class="card mt-4">
          <div class="card-header">Vue Axios Post Demo App</div>
          <div class="card-body">
            <form @submit.prevent="formSubmit">
              <strong>Name:</strong>
              <input type="text" class="form-control" v-model="name" />
              <strong>Description:</strong>
              <textarea class="form-control" v-model="description"></textarea>
              <button class="btn btn-success">Submit</button>
            </form>
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
        })
        .catch(function(error) {
          currentObj.output = error;
        });
    }
  }
};
</script>