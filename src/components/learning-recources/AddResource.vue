<template>
  <base-dialog v-if="inputIsInValid" title="Invalid Input" @close="confirmError ">
    <template #default>
      <p>Invalid input</p>
      <p>Check all inputs</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" type="text" name="title" ref="titleValue" />
      </div> 
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          type="text"
          name="description"
          rows="3"
          ref="descriptionValue"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" type="url" name="link" ref="linkValue" />
      </div>
      <div>
        <button type="submit">Add resource</button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ["addResource"],
  data() {
    return {
      inputIsInValid: false,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleValue.value;
      const enteredDescription = this.$refs.descriptionValue.value;
      const linkValue = this.$refs.linkValue.value;

      if (
        enteredTitle.trim() === "" ||
        enteredDescription.trim() === "" ||
        linkValue === ""
      ) {
        this.inputIsInValid = true;
        return
      }

      this.addResource(enteredTitle, enteredDescription, linkValue);
    },
    confirmError() {
      this.inputIsInValid = false;
    },
  },
};
</script>

<style script>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
