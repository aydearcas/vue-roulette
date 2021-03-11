<template>
  <div class="container">
    <div class="roulette">
      <div class="user" :class="isSelected(index)" v-for="(user, index) in users" :key="index">
        {{ user }}
      </div>
    </div>
    <div class="user-selected"> {{ userSelected }} </div>
    <button @click="spinRoulette">Tirar Ruleta</button>
  </div>
</template>

<script>
export default {
  name: 'BaseRoulette',
  data () {
    return {
      users: ['bruno', 'jose javier', 'carmen', 'juan pablo', 'roberto', 'adrian antonio', 'simon', 'sergio', 'ismael', 'irina', 'ricardo adrian', 'dario', 'lucia', 'carlos', 'antonio', 'mathias', 'nestor', 'aythami'],
      userSelected: -1
    };
  },
  methods: {
    getRandom () {
      return Math.floor(Math.random() * this.users.length);
    },
    spinRoulette () {
      // Aquí podemos poner un setInterval
      this.userSelected = this.getRandom();
    },
    isSelected (index) {
      return (index === this.userSelected) ? 'selected' : '';
    }
  },
  mounted () {
    console.log('mounted!');
  },
  updated () {
    console.log('updated!');
  }
};
</script>

<style lang="postcss">
.container {
    display: flex;
    flex-direction: column;
    justify-content: center;

  & .roulette {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 900px;
    margin: auto;

    & .user {
      border: 2px solid black;
      margin: 6px;
      padding: 6px;
      font-size: 36px;

      &.selected {
        background: red;
      }
    }
  }
  & .user-selected {
    display: flex;
    justify-content: center;
  }
}

</style>
