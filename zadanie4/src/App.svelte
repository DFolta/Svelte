<script>
  import avatar2 from './img/avatar2.png'
  import usersData from './data.json'

  let users = JSON.parse(JSON.stringify(usersData))

  let newUser = {
    id: null,
    name: '',
    avatar: avatar2,
    email: '',
    active: false,
  }

  let selectedOption = 'all'
  let isTableOpen = true
  let filteredUsersData = users
  let isOpen = true

  function deleteUser(id) {
    console.log(id)
    users = users.filter((user) => user.id !== id)
    refreshTable()
  }

  const filterUsers = (option) => {
    console.log(option)
    selectedOption = option
    refreshTable()
  }

  const refreshTable = () => {
    let filteredUsers
    switch (selectedOption) {
      case 'active':
        filteredUsers = users.filter((user) => user.active === true)
        break
      case 'inactive':
        filteredUsers = users.filter((user) => user.active === false)
        break
      default:
        filteredUsers = users
        break
    }
    $: filteredUsersData = filteredUsers
  }

  const toggleForm = () => {
    isOpen = !isOpen
  }

  let selectedActive = ''

  function handleChange(event) {
    selectedActive = event.target.value
  }

  const addUser = () => {
    if (newUser.name && newUser.email) {
      newUser.id = Math.floor(Math.random() * 100) + 1
      users = [...users, newUser]
      newUser = {
        id: null,
        name: '',
        avatar: '',
        email: '',
        active: false,
      }
      refreshTable()
    }
  }
</script>

<h1>List of User</h1>

<div class="setting">
  <div class="filter">
    <span>Filter users</span>
    <select
      bind:value={selectedOption}
      on:change={() => filterUsers(selectedOption)}
    >
      <option value="all">All users</option>
      <option value="active">Active users</option>
      <option value="inactive">Inactive users</option>
    </select>
  </div>
  <button class="addUser" on:click={() => toggleForm()}>New User</button>
</div>

{#if !isOpen}
  <div class="user-form">
    <form on:submit|preventDefault={addUser}>
      <div class="title">Create new user</div>
      <label>
        <p>Name:</p>
        <input type="text" bind:value={newUser.name} />
      </label>
      <label>
        <p>Email:</p>
        <input type="email" bind:value={newUser.email} />
      </label>
      <div class="isActive">
        Active:
        <span class="isActive"
          >Yes <input
            type="radio"
            bind:group={selectedActive}
            value="true"
            on:change={handleChange}
          /></span
        >
        <span class="isActive"
          >No<input
            type="radio"
            bind:group={selectedActive}
            value="false"
            on:change={handleChange}
          /></span
        >
      </div>
      <div class="formButton">
        <button class="buttonForm1" on:click={() => toggleForm()}>Close</button>
        <button class="buttonForm2" type="submit">Create</button>
      </div>
    </form>
  </div>
{/if}

<div class="users">
  {#if isTableOpen}
    {#each filteredUsersData as user}
      <table>
        <button
          class="buttonClose"
          on:click={() => {
            deleteUser(user.id)
          }}>X</button
        >
        <tr>
          <td class="number">{user.id}</td>
          <td><img src={user.avatar} alt={user.email} /></td>
          <td class="name">{user.name}</td>
          <td>{user.email}</td>
        </tr>
      </table>
    {/each}
  {/if}
</div>
