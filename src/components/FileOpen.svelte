<script>
  import { textStore } from "../stores/TextStores.js";

  let files;
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

<div>
  <input on:change={handleFileSelected} type="file" bind:files />
</div>

{#if files && files[0]}
  <p>
    {files[0].name}
  </p>
{/if}

<p>{content}</p>
