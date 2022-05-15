<script>
  import {
    Nav,
    NavbarBrand,
    NavItem,
    Dropdown,
    DropdownItem,
    DropdownToggle,
    DropdownMenu,
    NavLink,
    Image
  } from 'sveltestrap';

  import { push } from "svelte-spa-router"

  const linkHelp = "/help";
  const linkAbout ="/about"; 

</script>

<div class="nav-bar">
  <Nav dark>
    <NavbarBrand href="/">
      <img src="./sveltelogo.png" alt="svelte-logo"/>
    </NavbarBrand>
    <Dropdown dark nav inNavbar>
      <DropdownToggle nav caret>File</DropdownToggle>
      <DropdownMenu dark>
        <DropdownItem>Open File</DropdownItem>
        <DropdownItem>Save Text</DropdownItem>
        <DropdownItem divider />
        <DropdownItem>Clear Editor</DropdownItem>
      </DropdownMenu>
    </Dropdown>

    <!-- Navitems -->
    <NavItem>
      <NavLink on:click={() => push(linkHelp)}>Help</NavLink>
    </NavItem>
    <NavItem>
      <NavLink on:click={() => push(linkAbout)}>About</NavLink>
    </NavItem>
    <NavItem divider> | </NavItem>
  </Nav>
</div>


<style>

  img {
    height: 20px;
    padding-left: 1em;
  }

  /* .nav-bar {
    background-color: rgb(65, 5, 5);
    font-size: large;
    width: 100vh;
    outline: none;
    border: none;
    display: flex;
    flex-direction: row;
    align-items: center;
  } */

  :global(.nav-link) {
    color: orange !important;
  }

  :global(.dropdown-item) {
    color: orange !important;
  }
 
</style>