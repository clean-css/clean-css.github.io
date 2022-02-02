<script>
  import Icon from './Icon/Icon.svelte'
  import SettingsForm from './SettingsForm.svelte'

  let open = false

  const toggleOpen = () => {
    open = !open
  }
</script>

<div class="settings">
  <div class="d-flex justify-content-end">
    <button class="btn btn-outline-secondary mb-2 d-flex bg-light text-dark" on:click={toggleOpen}>
      <Icon name={open ? 'gear-highlighted' : 'gear'}/>
      <p class="m-0 ms-1">Settings</p>
    </button>
  </div>

  {#if open}
    <SettingsForm />
  {/if}
</div>

<style>
  .settings {
    width: 100%;
  }

  .settings :global(.icon) {
    font-size: 1.5em;
  }
</style>