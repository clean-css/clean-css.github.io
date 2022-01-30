<script>
  import Icon from './Icon/Icon.svelte'

  let className = ''

  export { className as class }
  export let onSavedToClipboard
  export let onSave

  const VALIDATION_ANIMATION_DURATION = 700
  const DOWNLOAD_MINIFIED_CSS = "Download minified css"
  const COPY_MINIFIED_CSS = "Copy minified css to clipboard"

  let isSavedToClipboard = false
  let isSaved = false

  const saveToClipboard = () => {
    isSavedToClipboard = true
    setTimeout(() => {
      isSavedToClipboard = false
    }, VALIDATION_ANIMATION_DURATION)

    onSavedToClipboard()
  }

  const save = () => {
    isSaved = true
    setTimeout(() => {
      isSaved = false
    }, VALIDATION_ANIMATION_DURATION)

    onSave()
  }
</script>

<div class={`d-flex ${className} copy-save-actions`}>
  <button
    class="btn btn-link p-1"
    title={COPY_MINIFIED_CSS}
    aria-label={COPY_MINIFIED_CSS}
    on:click={saveToClipboard}
  >
    <Icon name={isSavedToClipboard ? 'check' : 'clipboard'}/>
  </button>
  <button
    class="btn btn-link p-1 ms-1"
    title={DOWNLOAD_MINIFIED_CSS}
    aria-label={DOWNLOAD_MINIFIED_CSS}
    on:click={save}
  >
    <Icon name={isSaved ? 'check' : 'download'}/>
  </button>
</div>