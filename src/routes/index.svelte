<script lang="ts">
// @ts-ignore
import {HsvPicker} from 'svelte-color-picker';
 import Accordion, { Panel,Header, Content  } from '@smui-extra/accordion'; //Header, Content 
  import IconButton, { Icon } from '@smui/icon-button';
import Dialog, {  Content as DialogContent, Actions, Title} from '@smui/dialog'; 
  import Button, { Label } from '@smui/button';
 import  TopAppBar, { Row, Section, Title as AppTitle,  } from '@smui/top-app-bar';
import DrawerModal from "../components/modals/DrawerModal.svelte"


  let open = false;
  let panel1Open = false;
  let panel2Open = false;
  let panel3Open = false;
  let panel4Open = false;



function colorCallback(rgba:any) {
    console.log(rgba.detail)
}
</script>

<html>

  <div class="top-app-bar-container flexor">
    <TopAppBar
      variant="static"
      color={'secondary'}
    >
      <Row>
        <Section>
          <IconButton class="material-icons">menu</IconButton>
          <AppTitle>Design UI Palette Correction</AppTitle>
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
   
  </div>
  <DrawerModal/>
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

</html>

<style>
  .top-app-bar-container {
    /* max-width: 480px; */
    width: 100%;
    /* height: 320px; */
    border: 1px solid
      var(--mdc-theme-text-hint-on-background, rgba(0, 0, 0, 0.1));
    margin: 0 18px 18px 0;
    background-color: var(--mdc-theme-background, #fff);
 
    overflow: auto;
    display: inline-block;
  }
 html{
   padding: 0;
   margin: 0;
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

  .page-container{
    height: 100%;
    width: 100%;
    padding: 0;
    margin: 0;
  }


  /* These classes are only needed because the
    drawer is in a container on the page. */
  .drawer-container {
    position: relative;
    display: flex;
    height: 350px;
    max-width: 600px;
    border: 1px solid
      var(--mdc-theme-text-hint-on-background, rgba(0, 0, 0, 0.1));
    overflow: hidden;
    z-index: 0;
  }
 
  * :global(.app-content) {
    flex: auto;
    overflow: auto;
    position: relative;
    flex-grow: 1;
  }
 
  .main-content {
    overflow: auto;
    padding: 16px;
    height: 100%;
    box-sizing: border-box;
  }
</style>

