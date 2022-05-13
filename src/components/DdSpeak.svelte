<script>
  import { onMount } from "svelte";

  import { 
    Input, 
    Dropdown,
    DropdownItem,
    DropdownMenu,
    DropdownToggle
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
      <DropdownToggle nav caret>Speak</DropdownToggle>
      <DropdownMenu dark>
        <DropdownItem on:click={play} color="dark">Speak</DropdownItem>
        <DropdownItem divider />
          <Input bind:value={selectedVoice} type="select" id="voices">
            {#each voices as voice}
              <option value={voice}>{printVoice(voice)}</option>
            {/each}
          </Input>
          
      </DropdownMenu>
    </Dropdown>


