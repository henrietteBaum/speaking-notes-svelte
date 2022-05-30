<script>
  import HelpMenu from "./HelpMenu.svelte";
</script>

<div class="about">
  <HelpMenu />

  <h1>About</h1>
  <hr />
  <div class="content">
    The Editor is a part of my project "Speaking Notes", which will show, how to
    create an Application for visual impared users. You can find nearly the same
    App, written with
    <ul />
    <li>
      JavaScript only, <a
        href="https://github.com/henrietteBaum/Speaking-Notes"
        target="_blank">GitHub: Speaking-Notes 1</a
      >
    </li>
    <li>
      React (plain text), <a
        href="https://github.com/henrietteBaum/Speaking-Notes-React"
        target="_blank">GitHub: Speaking-Notes-React 2</a
      >
    </li>
    <li>
      React and Electron, <a
        href="https://github.com/henrietteBaum/speaking-notes-erb"
        target="_blank">GitHub: speaking-notes-erb 3</a
      >
    </li>
    <li>
      React (Markdown), <a
        href="https://github.com/henrietteBaum/Speaking-Notes-MD"
        target="_blank">GitHub: Speaking-Notes-MD 4</a
      >
    </li>
    <br />
    on my GitHub Repositories.

    <hr />
    Homepage:<a
      href="https://github.com/henrietteBaum/henrietteBaum.github.io"
      target="_blank">henrietteBaum.github.io</a
    >
    <br />
    Copyright © 2022 Henriette Baum
  </div>
</div>

<style>
  .about {
    width: 100%;
    height: 100vh;
    background-color: rgb(50, 51, 59);
    color: white;
    border: none;
    outline: none;
  }

  h1 {
    padding-top: 1em;
    color: orange;
  }
  .content {
    background-color: rgb(86, 1, 1);
    color: white;
    text-align: left;
    padding: 2em;
    margin: 0 3em;
    border-radius: 8px;
  }
</style>
