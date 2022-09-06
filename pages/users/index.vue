<template>
  <section>
    <h1>Users page</h1>
    <ul>
      <li v-for="(user, i) of 5" :key="i">
        <a href="#" @click.prevent="openUser(user)">User {{ user }}</a>
      </li>
    </ul>
  </section>
</template>
<script>
export default {
  methods:{
    openUser(user){
      this.$router.push(`/users/${user}`)

    }
  }
};
</script>

