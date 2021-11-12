<template>
  <base-card>
    <form>
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" name="title" :v-mode="title" />
      </div>
      <div class="form-control">
        <label for="desc">Description</label>
        <textarea id="desc" name="desc" rows="3" :v-model="desc"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" id="link" name="link" :v-model="link" />
      </div>
      <div>
        <base-button :type="submit" @click="formSubmit"> Submit </base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      desc: '',
      link: '',
    };
  },
  methods: {
    formSubmit(e) {
      e.preventDefault();
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
