<template>
  <base-dialog v-if="error" :title="error" @close="confirmError">
    <template #secondary>
      <p>Unfortunatly one input value is invalid</p>
    </template>
    <template #main> </template>
    <template #actions>
      <base-button @click="confirmError">OK</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="formSubmit">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" name="title" ref="title" />
      </div>
      <div class="form-control">
        <label for="desc">Description</label>
        <textarea id="desc" name="desc" rows="3" v-model="desc"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" id="link" name="link" ref="link" />
      </div>
      <div>
        <base-button :type="submit" @click="formSubmit"> Submit </base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog, BaseButton },
  data() {
    return {
      desc: '',
      error: '',
    };
  },
  inject: ['addResources'],
  methods: {
    confirmError() {
      this.error = '';
    },
    formSubmit() {
      const enteredTitle = this.$refs.title.value;
      const enteredLink = this.$refs.link.value;
      const errorCheck = () => {
        const errors = {
          title: enteredTitle,
          description: this.desc,
          url: enteredLink,
        };
        for (const keys in errors) {
          console.log(errors[keys].trim());
          if (errors[keys].trim().length === 0) {
            this.error = keys;
          }
        }
      };
      errorCheck();
      if (this.error) {
        return;
      }
      this.addResources({
        title: enteredTitle,
        desc: this.desc,
        url: enteredLink,
      });
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
