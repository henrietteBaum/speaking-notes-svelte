# Wiki / Documentation

## routing

Svelte-SPA-router

Routing in App.svelte:
```js
	<nav>
		<a href="/#/">Editor</a>
		<a href="/#/help">Help</a>
		<a href="/#/about">About</a>
	</nav> 
```
Instead of setting up a navigation in App.svelte I habe used **Sveltestrap** in a separate component `EditorMenu`, because I want to use the Dropdown from Sveltestrap.

For routing to Help and About I put a button inside my sveltestrap-Nav, which liks to the components. Found this example:

[Stackoverflow:](https://stackoverflow.com/questions/65649357/svelte-pass-useaction-to-component-child)

```svelte
<script>
  import { Button } from 'sveltestrap';
  import { push } from 'svelte-spa-router';
  let myLink = '/foo/bar';
</script>

<Button on:click={() => push(myLink)}>
  Click here
</Button>
```

And in my EditorMenu:

```html
<script>
  import { push } from "svelte-spa-router"

  const linkHelp = "/help";
  const linkAbout ="/about"; 
  </script>

<Nav>
<!-- ... -->
  <NavItem>
    <button on:click={() => push(linkHelp)}>Help</button>
  </NavItem>
  <NavItem>
    <button on:click={() => push(linkAbout)}>About</button>
  </NavItem>
<!-- ... -->
</Nav>
```

## File Input



## Sveltestrap Input 

```html
 <FormGroup>
  <Label for="exampleFile">File</Label>
  <Input type="file" name="file" id="exampleFile" />
  <FormText color="muted">
    This is some placeholder block-level help text for the above input. It's a
    bit lighter and easily wraps to a new line.
  </FormText>
</FormGroup>


<FormGroup>
  <Label for="exampleCustomFileBrowser">File Browser</Label>
  <CustomInput type="file" id="exampleCustomFileBrowser" name="customFile" />
</FormGroup>
<FormGroup>
  <Label for="exampleCustomFileBrowser">File Browser with Custom Label</Label>
  <CustomInput
    type="file"
    id="exampleCustomFileBrowser"
    name="customFile"
    label="Yo, pick a file!" />
</FormGroup>

```

## FileReader

Basic Example:

```js
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

```


## Speech Synthesis

```js
<script>
    import { onMount } from "svelte";
  
    import {
      Col,
      Container,
      Row,
      Input,
      Label,
      FormGroup,
      Button,
    } from "sveltestrap";
  
    export let voices = [];
    let pitch = 1;
    let rate = 1;
    let volume = 1;
    export let mdText;
    export let selectedVoice;
  
    onMount(() => {
      speechSynthesis.onvoiceschanged = () => {
        voices = speechSynthesis.getVoices();
        selectedVoice = voices[0];
      };
    });
  
    function play() {
      speechSynthesis.cancel();
  
      const utterance = new SpeechSynthesisUtterance(mdText);
  
      utterance.voice = selectedVoice;
    //   utterance.rate = rate;
    //   utterance.pitch = pitch;
    //   utterance.volume = volume;
      speechSynthesis.speak(utterance);
    }
  
    function printVoice(voice) {
      if (!voice) {
        return "";
      }
      return `${voice.name} (${voice.lang})`;
    }
  </script>
  
  <Container>
     <!-- <Row>
        <FormGroup>
          <Label for="words">Say Something</Label>
          <Input id="words" bind:value={mdText} />
        </FormGroup>
    </Row> -->
    <Row>
      <Col>
        <FormGroup>
          <Label for="voices">Voices</Label>
          <Input bind:value={selectedVoice} type="select" id="voices">
            {#each voices as voice}
              <option value={voice}>{printVoice(voice)}</option>
            {/each}
          </Input>
        </FormGroup>
      </Col>
    </Row>
    <!-- <Row>
      <Col>
        <FormGroup>
          <Label for="pitch">Pitch</Label>
          <Input
            bind:value={pitch}
            type="range"
            id="pitch"
            min="0.1"
            max="2"
            step=".1"
          />
        </FormGroup>
      </Col>
    </Row>
    <Row>
      <Col>
        <FormGroup>
          <Label for="rate">Rate</Label>
          <Input
            type="range"
            bind:value={rate}
            id="rate"
            min="0.1"
            max="2"
            step=".1"
          />
        </FormGroup>
      </Col>
    </Row>
  
    <Row>
      <Col>
        <FormGroup>
          <Label for="rate">Volume</Label>
          <Input
            type="range"
            bind:value={volume}
            id="volume"
            min="0.1"
            max="1"
            step=".1"
          />
        </FormGroup>
      </Col>
    </Row> -->
    <Row>
      <Col>
        <FormGroup>
          <Button on:click={play} color="dark">Play</Button>
        </FormGroup>
      </Col>
    </Row>
    <Row>
      <Col>
        Pitch: {pitch} | Speed: {rate} | Volume: {volume} | voice: {printVoice(
          selectedVoice
        )}
      </Col>
    </Row>
  </Container>
```

