<script lang="ts">
// @ts-ignore
import {HsvPicker} from 'svelte-color-picker';
 import Accordion, { Panel, Header, Content } from '@smui-extra/accordion';
  import IconButton, { Icon } from '@smui/icon-button';
import Dialog, { Title, Content as DialogContent, Actions } from '@smui/dialog';
  import Button, { Label } from '@smui/button';
 import  TopAppBar, { Row, Section, Title as AppTitle,  } from '@smui/top-app-bar';
  import Checkbox from '@smui/checkbox';
 import FormField from '@smui/form-field';
 
  let prominent = false;
  let dense = false;
  let secondaryColor = false;

  let open = false;
  let clicked = 'Nothing yet.';
 
  let panel1Open = false;
  let panel2Open = false;
  let panel3Open = false;
  let panel4Open = false;

function colorCallback(rgba:any) {
    console.log(rgba.detail)
}
</script>
<HsvPicker on:colorChange={colorCallback} startColor={"#FBFBFB"}/>
<h1>Welcome to SvelteKit</h1>
<div class="accordion-container">
  <Accordion>
    <Panel bind:open={panel1Open}>
      <Header>
        Panel 1
        <IconButton slot="icon" toggle pressed={panel1Open}>
          <Icon class="material-icons" on>expand_less</Icon>
          <Icon class="material-icons">expand_more</Icon>
        </IconButton>
      </Header>
      <Content>The content for panel 1.</Content>
    </Panel>
    <Panel bind:open={panel2Open}>
      <Header>
        Panel 2
        <IconButton slot="icon" toggle pressed={panel2Open}>
          <Icon class="material-icons" on>expand_less</Icon>
          <Icon class="material-icons">expand_more</Icon>
        </IconButton>
      </Header>
      <Content>The content for panel 2.</Content>
    </Panel>
    <Panel bind:open={panel3Open}>
      <Header>
        Panel 3
        <span slot="description">Description of panel 3.</span>
        <IconButton slot="icon" toggle pressed={panel3Open}>
          <Icon class="material-icons" on>expand_less</Icon>
          <Icon class="material-icons">expand_more</Icon>
        </IconButton>
      </Header>
      <Content>The content for panel 3.</Content>
    </Panel>
    <Panel bind:open={panel4Open}>
      <Header>
        Panel 4
        <span slot="description">Description of panel 4.</span>
        <IconButton slot="icon" toggle pressed={panel4Open}>
          <Icon class="material-icons" on>expand_less</Icon>
          <Icon class="material-icons">expand_more</Icon>
        </IconButton>
      </Header>
      <Content>The content for panel 4.</Content>
    </Panel>
  </Accordion>


   
<Button on:click={() => (open = true)}>
  <Label>Open Dialog</Label>
</Button>
 
<pre class="status">Clicked: {clicked}</pre>

<Dialog
  bind:open
  aria-labelledby="simple-title"
  aria-describedby="simple-content"
>
  <!-- Title cannot contain leading whitespace due to mdc-typography-baseline-top() -->
  <Title id="simple-title">Dialog Title</Title>
  <DialogContent id="simple-content">Super awesome dialog body text?</DialogContent>
  <Actions>
    <Button on:click={() => (clicked = 'No')}>
      <Label>No</Label>
    </Button>
    <Button on:click={() => (clicked = 'Yes')}>
      <Label>Yes</Label>
    </Button>
  </Actions>
</Dialog>
 
</div>

<div>
  <FormField>
    <Checkbox bind:checked={prominent} />
    <span slot="label">Prominent</span>
  </FormField>
  <FormField>
    <Checkbox bind:checked={dense} />
    <span slot="label">Dense</span>
  </FormField>
  <FormField>
    <Checkbox bind:checked={secondaryColor} />
    <span slot="label">Secondary</span>
  </FormField>
</div>
 
<div class="flexy">
  <div class="top-app-bar-container">
    <TopAppBar
      variant="static"
      {prominent}
      {dense}
      color={secondaryColor ? 'secondary' : 'primary'}
    >
      <Row>
        <Section>
          <IconButton class="material-icons">menu</IconButton>
          <Title>Static</Title>
        </Section>
        <Section align="end" toolbar>
          <IconButton class="material-icons" aria-label="Download"
            >file_download</IconButton
          >
          <IconButton class="material-icons" aria-label="Print this page"
            >print</IconButton
          >
          <IconButton class="material-icons" aria-label="Bookmark this page"
            >bookmark</IconButton
          >
        </Section>
      </Row>
    </TopAppBar>
    <div>
     ghvhgvhgvghvhgvhgv
      <img
        alt="Page content placeholder"
        src="/page-content.jpg"
        style="display: block; max-width: 100%; height: auto; margin: 1em auto;"
      />
    </div>
  </div>
 
  <div class="top-app-bar-container flexor">
    <TopAppBar
      variant="static"
      {prominent}
      {dense}
      color={secondaryColor ? 'secondary' : 'primary'}
    >
      <Row>
        <Section>
          <IconButton class="material-icons">menu</IconButton>
          <AppTitle>Flex Static</AppTitle>
        </Section>
        <Section align="end" toolbar>
          <IconButton class="material-icons" aria-label="Download"
            >file_download</IconButton
          >
          <IconButton class="material-icons" aria-label="Print this page"
            >print</IconButton
          >
          <IconButton class="material-icons" aria-label="Bookmark this page"
            >bookmark</IconButton
          >
        </Section>
      </Row>
    </TopAppBar>
    <div class="flexor-content">
      <img
        alt="Page content placeholder"
        src="/page-content.jpg"
        style="display: block; max-width: 100%; height: auto; margin: 1em auto;"
      />
    </div>
  </div>
</div>
<style>
  .top-app-bar-container {
    max-width: 480px;
    width: 100%;
    height: 320px;
    border: 1px solid
      var(--mdc-theme-text-hint-on-background, rgba(0, 0, 0, 0.1));
    margin: 0 18px 18px 0;
    background-color: var(--mdc-theme-background, #fff);
 
    overflow: auto;
    display: inline-block;
  }
 
  @media (max-width: 480px) {
    .top-app-bar-container {
      margin-right: 0;
    }
  }
 
  .flexy {
    display: flex;
    flex-wrap: wrap;
  }
 
  .flexor {
    display: inline-flex;
    flex-direction: column;
  }
 
  .flexor-content {
    flex-basis: 0;
    height: 0;
    flex-grow: 1;
    overflow: auto;
  }
</style>

