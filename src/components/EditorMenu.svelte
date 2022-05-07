<script>
  import {
    Nav,
    NavItem,
    Dropdown,
    DropdownItem,
    DropdownToggle,
    DropdownMenu,
    NavLink
  } from 'sveltestrap';

  import { push } from "svelte-spa-router"

  const linkHelp = "/help";
  const linkAbout ="/about"; 

</script>

<div class="nav-bar">
  <Nav dark>
  
    <Dropdown dark nav inNavbar>
      <DropdownToggle nav caret>File</DropdownToggle>
      <DropdownMenu dark>
        <DropdownItem>Open File</DropdownItem>
        <DropdownItem>Save Text</DropdownItem>
        <DropdownItem divider />
        <DropdownItem>Clear Editor</DropdownItem>
      </DropdownMenu>
    </Dropdown>

    <Dropdown dark nav inNavbar>
      <DropdownToggle nav caret>Speak</DropdownToggle>
      <DropdownMenu dark>
        <DropdownItem>Speak Text</DropdownItem>
        <DropdownItem>Pause</DropdownItem>
        <DropdownItem>Stop</DropdownItem>
        <DropdownItem divider />
        <DropdownItem>Clear Editor</DropdownItem>
      </DropdownMenu>
    </Dropdown>
    <!-- Navitems -->
    <NavItem>
      <button on:click={() => push(linkHelp)}>Help</button>
    </NavItem>
    <NavItem>
      <button on:click={() => push(linkAbout)}>About</button>
    </NavItem>
  </Nav>
</div>



<style>

  button {
    background-color: transparent;
    color: orange;
    border: none;
    padding-left: 1.7em;
  }

  button:hover {
    text-decoration: underline;
  }
  .nav-bar {
    background-color: rgb(65, 5, 5);
    font-size: large;
    width: 100vh;
    outline: none;
    border: none;
  }

  :global(.nav-link) {
    color: orange !important;
  }

  :global(.dropdown-item) {
    color: orange !important;
  }
 
</style>