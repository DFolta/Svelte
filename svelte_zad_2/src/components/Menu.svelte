<script>
  let isOpen = false
  let dropdown

  function toggleDropdown() {
    isOpen = !isOpen
  }

  let activeButtonId = null

  function setActiveButton(id) {
    activeButtonId = id
  }
</script>

<main>
  <div class="dropdown">
    <div class="header">
      <span class="title">Firma XxX</span>
      <svg
        fill="#ffffff"
        height="40px"
        width="40px"
        version="1.1"
        on:click={toggleDropdown}
        on:keydown
        id="Layer_1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        viewBox="0 0 297 297"
        xml:space="preserve"
      >
        <g>
          <g>
            <g>
              <path
                d="M280.214,39.211H16.786C7.531,39.211,0,46.742,0,55.997v24.335c0,9.256,7.531,16.787,16.786,16.787h263.428
				c9.255,0,16.786-7.531,16.786-16.787V55.997C297,46.742,289.469,39.211,280.214,39.211z"
              />
              <path
                d="M280.214,119.546H16.786C7.531,119.546,0,127.077,0,136.332v24.336c0,9.255,7.531,16.786,16.786,16.786h263.428
				c9.255,0,16.786-7.531,16.786-16.786v-24.336C297,127.077,289.469,119.546,280.214,119.546z"
              />
              <path
                d="M280.214,199.881H16.786C7.531,199.881,0,207.411,0,216.668v24.335c0,9.255,7.531,16.786,16.786,16.786h263.428
				c9.255,0,16.786-7.531,16.786-16.786v-24.335C297,207.411,289.469,199.881,280.214,199.881z"
              />
            </g>
          </g>
        </g>
      </svg>
    </div>
    <div class="content" class:open={isOpen} bind:this={dropdown}>
      <ul>
        <li
          on:click={() => setActiveButton(1)}
          on:click={toggleDropdown}
          class:active={activeButtonId === 1}
          on:keypress
        >
          HOME
        </li>
        <li
          on:click={() => (setActiveButton(2), toggleDropdown)}
          on:click={toggleDropdown}
          class:active={activeButtonId === 2}
          on:keypress
        >
          O NAS
        </li>
        <li
          on:click={() => (setActiveButton(3), toggleDropdown)}
          on:click={toggleDropdown}
          class:active={activeButtonId === 3}
          on:keypress
        >
          PRODUKTY
        </li>
        <li
          on:click={() => (setActiveButton(4), toggleDropdown)}
          on:click={toggleDropdown}
          class:active={activeButtonId === 4}
          on:keypress
        >
          BLOG
        </li>
        <li
          on:click={() => (setActiveButton(5), toggleDropdown)}
          on:click={toggleDropdown}
          class:active={activeButtonId === 5}
          on:keypress
        >
          LOGOWANIE
        </li>
      </ul>
    </div>
  </div>
</main>

<style>
  main {
    width: 100%;
    margin: 0;
    font-family: 'Lucida Console', Monospace;
  }
  .title {
    font-size: 32px;
  }

  svg {
    color: #fff;
  }
  .dropdown {
    background-color: #000;
    color: #fff;
    position: relative;
    cursor: default;
  }
  ul {
    padding: 0;
  }

  li {
    cursor: pointer;
    font-size: 18px;
    font-family: 'Lucida Console', Monospace;
    list-style-type: none;
    padding: 16px;
    border-radius: 8px;
  }

  li:hover {
    text-decoration: underline;
    color: aquamarine;
    text-decoration-thickness: 2px;
    text-underline-offset: 6px;
  }

  .active {
    color: #000;
    background-color: aquamarine;
    text-decoration: none;
  }
  .active:hover {
    color: #000;
    background-color: aquamarine;
    text-decoration: none;
  }

  .header {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    border: 1px solid black;
    cursor: pointer;
  }

  .content {
    background-color: #000;
    color: #fff;
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s ease-in-out;
    text-align: center;
    display: flex;
    justify-content: center;
  }

  .content.open {
    max-height: 460px;
  }
</style>
