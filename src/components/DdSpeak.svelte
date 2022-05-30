<script>
  import { onMount } from "svelte";
  import { textStore } from "../stores/TextStores.js";
  import {
    Label,
    Input,
    Dropdown,
    DropdownItem,
    DropdownMenu,
    DropdownToggle,
  } from "sveltestrap";

  export let voices = [];
  let pitch = 1;
  let rate = 1;
  let volume = 1;
  export let selectedVoice;

  onMount(() => {
    speechSynthesis.onvoiceschanged = () => {
      voices = speechSynthesis.getVoices();
      selectedVoice = voices[0];
    };
  });

  function play() {
    speechSynthesis.cancel();

    const utterance = new SpeechSynthesisUtterance($textStore);
    utterance.voice = selectedVoice;
    speechSynthesis.speak(utterance);
  }

  function printVoice(voice) {
    if (!voice) {
      return "";
    }
    return `${voice.name} (${voice.lang})`;
  }
</script>

<Dropdown dark nav inNavbar>
  <DropdownToggle nav caret>Speak Text</DropdownToggle>
  <DropdownMenu dark>
    <DropdownItem on:click={play} color="dark">Speak</DropdownItem>
    <DropdownItem divider />
    <DropdownItem header>Select a voice</DropdownItem>
    <Label class="label" for="voices">Select a voice</Label>
    <Input class="input" bind:value={selectedVoice} type="select" id="voices">
      {#each voices as voice}
        <option value={voice}>{printVoice(voice)}</option>
      {/each}
    </Input>
  </DropdownMenu>
</Dropdown>

<style>
  option {
    background-color: #343a40;
    color: orange;
  }

  :global(.input) {
    background-color: #343a40;
    color: orange;
  }

  :global(.label) {
    color: transparent;
    height: 1px;
  }
</style>
