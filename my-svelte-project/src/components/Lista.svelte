<script>
  import data from './sd'
</script>

<table>
  <thead>
    <tr>
      <th>Identyfikator</th>
      <th>Avatar</th>
      <th>E-mail</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    {#each data.uzytkownicy as user}
      <tr>
        <td>{user.id}</td>
        <td><img src={user.avatar} alt={user.email} /></td>
        <td>{user.email}</td>
        <td>{user.status}</td>
      </tr>
    {/each}
  </tbody>
</table>
