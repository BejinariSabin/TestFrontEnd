<template>
  <div>
    <b-form
      class="contact container form-inline"
      @submit="onSubmit"
      @reset="onReset"
      v-if="show"
    >
      <div class="inputDiv">
        <b-form-input
        id="inputContact"
          v-model="form.name"
          type="text"
          placeholder="Enter your name"
          pattern="[A-Za-z]{1,}"
          style="margin-top:10px"
        ></b-form-input>
        <b-form-input
        id="inputContact"
          v-model="form.surname"
          type="text"
          placeholder="Enter your surname"
          pattern="[A-Za-z]{1,}"
        ></b-form-input>
        <b-form-input
        id="inputContact"
          v-model="form.number"
          type="number"
          placeholder="Enter your phone number"
        ></b-form-input>
        <b-form-input
        id="inputContact"
          v-model="form.email"
          type="email"
          placeholder="Enter your email"
        ></b-form-input>
      </div>
      <div class="buttonDiv">
        <b-button type="submit" @click="submitForm">Submit</b-button>
      </div>
    </b-form>

    <b-form-input
      v-model="msg"
      type="text"
      placeholder="output"
      style="width: 800px; align-self: center; margin: auto"
    ></b-form-input>
    <label>Names don't accept numbers</label>
    <br>
    <label>Phone number requires 10 digits</label>
    <br>
    <label>Email requires email@something.domain</label>
    
  </div>
</template>

<script>
export default {
  name: "ContactView",
  data() {
    return {
      form: { name: "", surname: "", email: "", number: "" },
      show: true,
      msg: "",
    };
  },
  methods: {
    submitForm() {
     
      if (
        this.form.name.length < 3 ||
        this.form.surname.length < 3 ||
        this.form.email.length < 3 ||
        this.form.number.length != 10
      )
        alert("Wrong input");
      else this.msg = JSON.stringify(this.form);
    },
    onSubmit(event) {
      event.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(event) {
      event.preventDefault();
      this.form.email = "";
      this.form.name = "";
      this.form.surname = "";
      this.form.number = "";
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>

<style>
#inputContact{
  margin-bottom: 5px;
}
.contact {
  display: inline-flex;
}
.inputDiv {
  width: 90%;
}
.buttonDiv {
  width: 10%;
  align-self: center;
  margin-left: 10px;
}
</style>
