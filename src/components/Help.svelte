<script>
  import HelpMenu from "./HelpMenu.svelte";
</script>

<HelpMenu />

<section>
  <h1>Markdown Reference:</h1>
  <hr />
  <div class="link">
    <a href="https://www.markdownguide.org/basic-syntax/">Marcdownguide.org</a>
  </div>
  <hr />
  <br />
  <h2>Headings:</h2>
  <p>
    # H1, ## H2, ### H3 one number-sign for every heading-level, one space
    between number-sign and your heading-text.
  </p>
  <h2>Bold text:</h2>
  <p>
    **some bold text inside two asterisk-sign, no space between symbo and your
    text.**
  </p>
  <h2>Blockquote:</h2>
  <p>
    &gt;your quote after one greater-than-sign at the beginning, no space
    between symbol and your text.
  </p>
  <h2>Unordered list:</h2>
  <p>-item</p>
  <p>-item</p>
  <p>-item</p>
  <h2>Ordered list:</h2>
  <p>1. item one</p>
  <p>2. item one</p>
  <p>3. item one</p>
  <h2>Code:</h2>
  <p>
    `some code, inside one backtick at the beginning and on end, you must press
    spacebar after setting the backtick!`
  </p>
  <h2>CodeBlock:</h2>
  <p>
    ```lang
    <br />
    some code inside three backticks, followd by the name of programming-language:
    lang e.g. js, ruby or java
    <br />
    ```
  </p>
  <h2>Link:</h2>
  <p>[title](https://www.example.com)</p>
  <h2>Image:</h2>
  <p>![alt text](image.jpg)</p>
</section>

<style>
  section {
    width: 100%;
    background-color: rgb(86, 1, 1);
    font-size: larger;
    color: white;
    text-align: left;
    padding: 2em;
  }

  h1 {
    color: orange;
    text-align: center;
  }

  a {
    color: orange;
    font-size: larger;
  }

  .link {
    text-align: center;
  }
</style>
