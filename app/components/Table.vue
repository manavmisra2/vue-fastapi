<template>
  <v-data-table :headers="headers" :items="users">
    <!-- <template v-slot:['item.edit' ]="{item}" > -->
      <v-btn color="primary" @click="editItem(item)">Edit</v-btn>

    <!-- </template> -->
</v-data-table>
</template>
<script>
  export default {
    data () {
      return {
        headers: [
          { text: 'Name', value: 'name' },
          { text: 'Email', value: 'email' },
          { text: 'Password', value: 'password' },
          { text: 'Edit', value: 'edit' },
          { text: 'Delete', value: 'delete' },
        ],
      }
    },
    computed: {
      users(){
        return this.$store.state.users.data
      }
    },
    async fetch()
    {
        this.$store.commit('users/storeData', (await this.$axios.get('https://localhost:8000')).data)

    }
  }
</script>
<style>

</style>