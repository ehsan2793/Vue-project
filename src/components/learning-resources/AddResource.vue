<template>
  <base-dialog v-if="invalidInput" title="Invalid Input" @close='closeDialog'>
    <template #default>
      <p>check you inputs One of them is empty</p>
        <p>if you dont want to check it I will check it</p>
    </template>
     <template #actions>
         <base-button @click="closeDialog">Ok</base-button>

     </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input
          type="text"
          id="title"
          name="title"
          placeholder="Enter Tiltle"
          ref="title"
        />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="description"
        >
        </textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="link" id="link" name="link" ref="link" />
      </div>

      <div>
        <base-button type="submit">Submit</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseCard from '../UI/BaseCard.vue';
export default {
  inject: ['addResource'],
  components: { BaseCard, BaseButton },
  data() {
    return {
      invalidInput: false,
    };
  },
  methods: {
      closeDialog(){
          this.invalidInput = false;
      },

    submitData() {
      const enterdTitle = this.$refs.title.value;
      const enterdDescription = this.$refs.description.value;
      const enterdLink = this.$refs.link.value;

      if (
        enterdTitle.trim() === '' ||
        enterdDescription.trim() === '' ||
        enterdLink.trim() === ''
      ) {
        this.invalidInput = true;
        return;
      }

      this.addResource(enterdTitle, enterdDescription, enterdLink);
    },
  },
};
</script>

<style scoped>
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
