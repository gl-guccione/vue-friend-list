<template>

  <form @submit.prevent="submitNewFriend">

    <div>
      <label for="name">Name</label>
      <input id="name" type="text" v-model="newFriend.name">
    </div>

    <div>
      <label for="phone">Phone</label>
      <input id="phone" type="tel" v-model="newFriend.phone">
    </div>

    <div>
      <label for="email">Email</label>
      <input id="email" type="text" v-model="newFriend.email">
    </div>

    <button>Add new friend</button>

  </form>

</template>

<script>
export default {
  data() {
    return {
      newFriend: {
        name: '',
        phone: '',
        email: ''
      }
    }
  },
  methods: {
    submitNewFriend() {
      if (this.newFriend.name != '' && this.newFriend.phone != '' && this.newFriend.email != '') {
        this.$emit('submit-new-friend', this.newFriend);
        this.newFriend.name = '';
        this.newFriend.phone = '';
        this.newFriend.email = '';
      }
    }
  }
}
</script>