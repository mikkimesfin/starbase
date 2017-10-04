<template>
  <div class="" @click="switchCharacter">
    {{character}}
  </div>
</template>

<script>

export default {
  props: ['id'],
  data () {
    return {
      character: {}
    }
  },
  methods: {
    fetchCharacter(id) {
      fetch(`https://cors-anywhere.herokuapp.com/http://swapi.co/api/people/${id}`, {
        method: 'GET'
      })
      .then(response => response.json())
      .then(json => this.character = json)
    },
    switchCharacter() {
      let random_id = Math.floor(Math.random() * 83) + 1
      this.fetchCharacter(random_id)
      //recall the function wth the new id.
    }
  },
  created() {
    this.fetchCharacter(this.id)
  }
}
</script>
