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