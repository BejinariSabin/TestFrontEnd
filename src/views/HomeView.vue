<template>
  <div class="home">
    <div class="table-wrapper homeTable">
      <table
        class="table table-hover table-bordered usersTable"
        style="overflow-y: auto"
      >
        <thead class="table-dark sticky">
          <tr>
            <th scope="col">Drink Name</th>
            <th scope="col">Category</th>
            <th scope="col">Tags</th>
            <th scope="col">Instructions</th>
            <th scope="col">Actions</th>
          </tr>
        </thead>
        <tbody>
          <!-- v-for drink,index in drinks key:drink.idDrinks -->
          <tr
            draggable="true"
            class="tableItem"
            v-for="item in itemList"
            :key="item.idDrink"
            ondragstart="start()"
            ondragover="dragover()"
          >
            <td>{{ item.strDrink }}</td>
            <td>{{ item.strCategory }}</td>
            <td>{{ item.strTags }}</td>
            <td>{{ item.strInstructions }}</td>
            <td>
              <div class="buttonDiv container">
                <b-button
                  v-b-modal.modal-add
                  class="addButton"
                  variant="success"
                  >Add</b-button
                >
                <b-button
                  v-b-modal.modal-edit
                  class="editButton"
                  variant="primary"
                  @click="editModal"
                  >Edit</b-button
                >
                <b-button
                  v-b-modal.modal-delete
                  class="deleteButton"
                  variant="danger"
                  >Delete</b-button
                >
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <b-modal id="modal-add" hide-footer title="Add modal">
      <b-form
        class="addFields container form-inline"
        @submit="onSubmit"
        @reset="onReset"
        v-if="show"
      >
        <div class="addDiv">
          <b-form-input
            id="inputField"
            v-model="form.strDrink"
            type="text"
            placeholder="Drink Name"
            pattern="[A-Za-z]{1,}"
          ></b-form-input>
          <b-form-input
            id="inputField"
            v-model="form.strCategory"
            type="text"
            placeholder="Category"
            pattern="[A-Za-z]{1,}"
          ></b-form-input>
          <b-form-input
            id="inputField"
            v-model="form.strTags"
            type="number"
            placeholder="Tags"
          ></b-form-input>
          <b-form-input
            id="inputField"
            v-model="form.strInstructions"
            type="email"
            placeholder="Instructions"
          ></b-form-input>
        </div>
        <div class="buttonDivAdd">
          <b-button type="submit" @click="submitForm">Submit</b-button>
        </div>
      </b-form>
    </b-modal>

    <b-modal id="modal-edit" hide-footer title="Add modal">
      <b-form
        class="addFields container form-inline"
        @submit="onSubmit"
        @reset="onReset"
        v-if="show"
      >
        <div class="addDiv">
          <b-form-input
            id="inputField"
            v-model="modal.strDrink"
            type="text"
            placeholder="Drink Name"
            pattern="[A-Za-z]{1,}"
          ></b-form-input>
          <b-form-input
            id="inputField"
            v-model="modal.strCategory"
            type="text"
            placeholder="Category"
            pattern="[A-Za-z]{1,}"
          ></b-form-input>
          <b-form-input
            id="inputField"
            v-model="modal.strTags"
            type="number"
            placeholder="Tags"
          ></b-form-input>
          <b-form-input
            id="inputField"
            v-model="modal.strInstructions"
            type="email"
            placeholder="Instructions"
          ></b-form-input>
        </div>
        <div class="buttonDivAdd">
          <b-button type="submit" @click="submitChanges"
            >Submit changes</b-button
          >
        </div>
      </b-form>
    </b-modal>

    <b-modal id="modal-delete" hide-footer title="Delete modal">
      <div class="d-block text-center">
        <h3>Are you sure you want to delete this row?</h3>
      </div>
      <b-button
        id="deleteOption"
        class="mt-3"
        variant="outline-danger"
        block
        @click="chooseDecline"
        >No</b-button
      >
      <b-button
        id="deleteOption"
        class="mt-3"
        variant="outline-success"
        block
        @click="chooseAccept"
        >Yes</b-button
      >
    </b-modal>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  props: ["drinks"],
  data() {
    return {
      show: true,
      form: {
        strDrink: "",
        strCategory: "",
        strTags: "",
        strInstructions: "",
      },
      modal: {
        strDrink: "",
        strCategory: "",
        strTags: "",
        strInstructions: "",
      },
      itemList: [
        {
          strDrink: "drinkName",
          strCategory: "category",
          strTags: "tag",
          strInstructions: "instruction",
        },
        {
          strDrink: "drinkName",
          strCategory: "category",
          strTags: "tag",
          strInstructions: "instruction",
        },
        {
          strDrink: "drinkName",
          strCategory: "category",
          strTags: "tag",
          strInstructions: "instruction",
        },
        {
          strDrink: "drinkName",
          strCategory: "category",
          strTags: "tag",
          strInstructions: "instruction",
        },
      ],
    };
  },
  
  mounted: {
    /* async getDrinks() {
      const drinks = await fetch("https://www.thecocktaildb.com/api/json/v1/1/search.php?s=margarita");
      drinks.data.forEach((drink,index) => {
        drinks.data[index]
      })
    } */
  },
  methods: {
    
    /* start(event) {
      var row;
      row = event.target;
    },
    dragover(event) {
      var e = event;
      e.preventDefault();

      let children = Array.from(e.target.parentNode.parentNode.children);
      if (children.indexOf(e.target.parentNode) > children.indexOf(row))
        e.target.parentNode.after(row);
      else e.target.parentNode.before(row);
    }, */
    editModal(id) {
      const drink = this.drinks.drink.find((drink) => drink.idDrink === id);
      console.log("drink", drink);
      if (drink) {
        this.modal.strDrink = drink.strDrink;
        this.modal.strCategory = drink.strCategory;
        this.modal.strTags = drink.strTags;
        this.modal.strInstructions = drink.strInstructions;
      }
    },
    submitChanges() {
      if (
        this.modal.strDrink.length < 3 ||
        this.modal.strCategory.length < 1 ||
        this.modal.strTags.length < 3 ||
        this.modal.strInstructions.length < 1
      )
        alert("Wrong input");
      /*  edit the values after submiting
        else {
          const drinks= {
           idDrink: this.drinks.idDrink,
           strDrink: this.modal.strDrink,
           strCategory: this.modal.strCategory,
           strTags: this.modal.strTags,
           strInstructions: this.modal.strInstructions,
          };
          await put(drinks)
        } */
    },
    submitForm() {
      if (
        this.form.strDrink.length < 3 ||
        this.form.strCategory.length < 1 ||
        this.form.strTags.length < 3 ||
        this.form.strInstructions.length < 1
      )
        alert("Wrong input");
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
    chooseDecline() {
      this.$bvModal.hide("modal-delete");
    },
    chooseAccept() {
      // delete the item from the table
    },
  },
};
</script>

<style>
.addButton,
.editButton,
.deleteButton {
  margin-left: 4px;
}
.addDiv {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: space-between;
}
#inputField {
  margin-bottom: 5px;
}
#modal-delete {
  display: flex;
  align-content: space-between;
}
#deleteOption {
  margin: 0px 5px 0px 0px;
}
</style>
