<template>
  <div class="product-info">
    <div class="pricing-header px-3 py-3 pt-md-5 pb-md-4 mx-auto text-center">
      <h3 class="display-5">Product Infomation</h3>
      <router-link to="/product">Back</router-link>
    </div>

    <div class="container">
      <form @submit.prevent="save()">
        <div class="form-group row">
          <label for="inputPassword" class="col-sm-3 col-form-label"
            >Product name</label
          >
          <div class="col-sm-9">
            <input
              @blur="validate()"
              type="text"
              class="form-control"
              v-model="product.name"
              v-bind:class="{ 'is-invalid': errors.name }"
            />
            <div class="invalid-feedback text-left" v-if="errors.name">
              {{ errors.name }}
            </div>
          </div>
        </div>
        <div class="form-group row">
          <label for="inputPassword" class="col-sm-3 col-form-label"
            >Product price</label
          >
          <div class="col-sm-9">
            <input
              @blur="validate()"
              type="text"
              class="form-control"
              v-model="product.price"
              v-bind:class="{ 'is-invalid': errors.price }"
            />
            <div class="invalid-feedback text-left" v-if="errors.price">
              {{ errors.price }}
            </div>
          </div>
        </div>
        <div class="form-group row">
          <label for="inputPassword" class="col-sm-3 col-form-label"
            >Product description</label
          >
          <div class="col-sm-9">
            <textarea
              @blur="validate()"
              class="form-control"
              rows="3"
              v-model="product.description"
              v-bind:class="{ 'is-invalid': errors.description }"
            ></textarea>
            <div class="invalid-feedback text-left" v-if="errors.description">
              {{ errors.description }}
            </div>
          </div>
        </div>
        <div class="form-group row">
          <label for="inputPassword" class="col-sm-3 col-form-label"></label>
          <div class="col-sm-9 text-left">
            <button type="submit" class="btn btn-primary">Save</button> &nbsp;
            <button type="reset" class="btn btn-danger">Cancel</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "productForm",
  data() {
    return {
      errors: {
        name: "",
        price: "",
        description: "",
      },
      product: {
        name: "",
        price: "",
        description: "",
      },
    };
  },
  methods: {
    validate() {
      var isValid = true;
      this.errors = {
        name: "",
        price: "",
        description: "",
      };

      if (!this.product.name) {
        this.errors.name = "Name is required!!!";
        isValid = false;
      }

      if (!this.product.price) {
        this.errors.price = "Price is required!!!";
        isValid = false;
      } else if (isNaN(this.product.price)) {
        this.errors.price = "Price must be number!!!";
        isValid = false;
      }

      if (!this.product.description) {
        this.errors.description = "Description is required!!!";
        isValid = false;
      }

      return isValid;
    },
    save() {
      this.validate();
      console.log(this.validate());
    },
  },
};
</script>
