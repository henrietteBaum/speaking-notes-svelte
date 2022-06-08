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
  import { textStore, fileName } from "../stores/TextStores.js";

  const linkHelp = "/help";
  const linkAbout = "/about";

  let content;

  const handleFileSelected = (e) => {
    let file = e.target.files[0];
    $fileName = file.name;
    console.log($fileName);
    let reader = new FileReader();
    reader.readAsText(file);
    reader.onload = (e) => {
      content = e.target.result;
      $textStore = content;
    };
    // console.log({ $textStore });
  };

  function handleSaveFile(filename) {
    const blob = new Blob([$textStore], {type: 'text/plain'});
    const url = URL.createObjectURL(blob);
    const link = document.createElement('a');
    link.download = filename || 'untitled.md';
    link.href = url;
    link.click();
    URL.revokeObjectURL(url); 
}

function handleClearEditor() {
  $textStore = '';
}
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
        <DropdownItem on:click={handleSaveFile($fileName)} >Save Text</DropdownItem>
        <DropdownItem divider />
        <DropdownItem on:click={handleClearEditor}>Clear Editor</DropdownItem>
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
