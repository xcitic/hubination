<template>
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th scope="col">Rank</th>
        <th scope="col">Name</th>
        <th scope="col">Stars</th>
        <th scope="col">Avatar</th>
        <th scope="col">Github Link</th>
        <th scope="col">Homepage</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="repo in showRepos" :key="repo.id" class="mt-2">
        <th scope="row">
          {{ repositories.indexOf(repo) + 1 }}
        </th>
        <td>
          {{ repo.name }}
        </td>
        <td>
          {{ repo.stargazers_count.toLocaleString() }}
        </td>
        <td>
          <img v-if="repo.owner.avatar_url" class="avatar" :src="repo.owner.avatar_url"/>
        </td>
        <td>
          <a :href="repo.html_url" target="_blank">Link</a>
        </td>
        <td>
          <a v-if="repo.homepage" :href="repo.homepage" target="_blank">Homepage</a>
          <p v-else>No homepage</p>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'DataTable',
  props: {
    repositories: Array,
    showRepos: Array
  }
}
</script>

<style scoped>
  .avatar {
    max-width: 50px;
  }
</style>
