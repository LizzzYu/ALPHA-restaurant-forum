<template>
  <div class="container py-5">
    <form @submit.stop.prevent="handleSubmit">
      <div class="form-group">
        <label for="name">Name</label>
        <input
          id="name"
          v-model="name"
          type="text"
          name="name"
          class="form-control"
          placeholder="Enter Name"
          required
        />
      </div>

      <div class="form-group">
        <label for="image">Image</label>
        <img
          v-if="image"
          :src="image"
          class="d-block img-thumbnail mb-3"
          width="200"
          height="200"
        />
        <input
          id="image"
          type="file"
          name="image"
          accept="image/*"
          class="form-control-file"
          @change="handleFileChange"
        />
      </div>

      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script>
const dummyData = {
  // id: 1,
  name: '77',
  image: 'https://i.imgur.com/58ImzMM.png'
};

export default {
  name: 'UserEdit',
  data() {
    return {
      name: '',
      image: '',
    };
  },
  mounted() {
    const {id: userId} = this.$route.params
    this.fetchUser(userId);
  },
  methods: {
    // fetchUser(userId) {
    fetchUser() {
      const { name, image } = dummyData;
    this.name = name
    this.image = image
    },
    handleFileChange(e) {
      const { files } = e.target;

      if (files.length === 0) {
        this.image = '';
      } else {
        const imgURL = window.URL.createObjectURL(files[0]);
        this.image = imgURL;
      }
    },
    handleSubmit(e) {
      const form = e.target;
      const formData = new FormData(form);

      for (let [name, value] of formData.entries()) {
        console.log(name + ':' + value)
      }
      // this.$emit('after-submit', formData)
    },
  },
};
</script>
