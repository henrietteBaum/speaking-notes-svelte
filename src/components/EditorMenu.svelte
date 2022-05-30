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
  } from "sveltestrap";

  import { push } from "svelte-spa-router";
  import { textStore } from "../stores/TextStores.js";

  const linkHelp = "/help";
  const linkAbout = "/about";

  let content;

  const handleFileSelected = (e) => {
    let file = e.target.files[0];
    let reader = new FileReader();
    reader.readAsText(file);
    reader.onload = (e) => {
      content = e.target.result;
      $textStore = content;
    };
    console.log({ $textStore });
  };
</script>

<div class="nav-bar">
  <Nav dark>
    <NavbarBrand href="/">
      <img src="./sveltelogo.png" alt="svelte-logo" />
    </NavbarBrand>
    <Dropdown dark nav inNavbar>
      <DropdownToggle nav caret>File</DropdownToggle>
      <DropdownMenu dark>
        <DropdownItem>
          <label for="file-input">Open File</label>
          <input
            on:change={handleFileSelected}
            type="file"
            class="file-input"
            id="file-input"
          />
        </DropdownItem>
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
    <NavItem divider />
  </Nav>
</div>

<style>
  .file-input {
    display: none;
  }

  img {
    height: 20px;
    padding-left: 1em;
  }

  :global(.nav-link) {
    color: orange !important;
  }

  :global(.dropdown-item) {
    color: orange !important;
  }
</style>
