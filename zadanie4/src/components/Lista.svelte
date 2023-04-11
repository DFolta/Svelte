<script>
  import usersData from '../data.json'

  let selectedOption = 'all'
  let isTableOpen = true

  const filterUsers = (option) => {
    switch (option) {
      case 'active':
        return usersData.uzytkownicy.filter((user) => user.active === true)
      case 'inactive':
        return usersData.uzytkownicy.filter((user) => user.active === false)
      default:
        return usersData.uzytkownicy
    }
  }
  function toggleTable(id) {
    isTableOpen[id] = !isTableOpen[id]
  }
</script>

<div class="filter">
  <span>Filter user</span>

  <select bind:value={selectedOption}>
    <option value="all">Wszyscy użytkownicy</option>
    <option value="active">Tylko aktywni</option>
    <option value="inactive">Tylko nieaktywni</option>
  </select>
</div>
{#each filterUsers(selectedOption) as user}
  {#if isTableOpen}
    <table>
      <tr>
        <td class="number">{user.id}</td>
        <td><img src={user.avatar} alt={user.email} /></td>
        <td>{user.name}</td>
        <td>{user.email}</td>
        <button class="close" on:click={() => toggleTable(user.id)}>X</button>
      </tr>
    </table>
  {/if}
{/each}

<style>
  select {
    background-color: #cccc;
    padding: 10px;
    border-radius: 4px;
  }
  table {
    background-color: #fff;
    color: #000;
    width: 100%;
    margin-top: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 2px 2px 5px #888888;
  }

  .number {
    padding: 10px;
    text-align: center;
  }
  .close {
    position: absolute;
    right: 15px;
    border-radius: 90px;
    background-color: coral;
    border-color: coral;
    color: #fff;
  }

  .filter {
    display: flex;
    gap: 20px;
  }
</style>
