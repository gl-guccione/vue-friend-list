<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>
    <new-friend-form
      @submit-new-friend="submitNewFriend"
    >

    </new-friend-form>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :key="friend.id"
        :id="friend.id"
        :name="friend.name"
        :phone-number="friend.phone"
        :email-address="friend.email"
        :is-favorite="friend.isFavorite"
        @toggle-favorite="toggleFavorite"
        @delete-friend="deleteFriend"
        >
      </friend-contact>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: 1,
          name: "Manuel Lorenz",
          phone: "0123 45678 90",
          email: "manuel@localhost.com",
          isFavorite: true
        },
        {
          id: 2,
          name: "Julie Jones",
          phone: "0987 654421 21",
          email: "julie@localhost.com",
          isFavorite: false
        },
        {
          id: 3,
          name: "Luca Guccione",
          phone: "43 4334435 12",
          email: "luca@localhost.com",
          isFavorite: true
        },
      ],
    };
  },
  methods: {
    toggleFavorite(friendId) {
      const selectedFriend = this.friends.find((friend) => friend.id == friendId);
      selectedFriend.isFavorite = !selectedFriend.isFavorite;
    },
    deleteFriend(friendId) {
      this.friends = this.friends.filter((friend) => friend.id != friendId);
    },
    submitNewFriend(friend) {
      const newFriend = {
        id: (this.friends[this.friends.length - 1].id) + 1,
        name: friend.name,
        phone: friend.phone,
        email: friend.email,
        isFavorite: false
      };
      this.friends.push(newFriend);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: 'Jost', sans-serif;
}
body {
  margin: 0;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#app li,
#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}
#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
</style>