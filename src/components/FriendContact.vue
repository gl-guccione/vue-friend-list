<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }} </h2>
    <button @click="toggleFavorite">{{ isFavorite ? 'Remove Favorite' : 'Make Favorite' }}</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="deleteFriend">Delete</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  // props: ['name', 'phoneNumber', 'emailAddress'],
  props: {
    name: {
      type: String,
      required: true,
    },
    phoneNumber: String,
    emailAddress: String,
    id: Number,
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      // validator: function (value) {
      //   return value === '1' || value === '0';
      // },

      // validator: value => value === '1' || value === '0',
    }
  },
  emits: [
    'toggle-favorite',
    'delete-friend'
  ],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit('toggle-favorite', this.id);
    },
    deleteFriend() {
      this.$emit('delete-friend', this.id);
    }
  }
};
</script>