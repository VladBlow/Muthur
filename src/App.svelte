<script>
  // Svelte
  import { onMount } from "svelte";

  // Stores
  import { isInput, viewMode } from "./stores/muthur";

  // Components
  import ViewPort from "./components/ViewPort.svelte";

  // Utils
  import createMenu from "./utils/menu";

  // Lifecycle
  onMount(() => createMenu(false));

  // Update
  $: {
    const isCreateMenu =
      $viewMode === `tasks` ||
      $viewMode === `terms` ||
      $viewMode === `divisions` ||
      $viewMode === `types` ||
      $viewMode === `logs`;

    createMenu(isCreateMenu, $isInput);
  }
</script>

<style type="text/scss">
  :global(html) {
    scroll-behavior: smooth;
  }

  :global(body) {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: stretch;
    width: 100vw;
    min-height: 100vh;
    margin: 0;
    padding: 0;
    font-family: "iosevka", "Courier New", Courier, monospace;
    font-size: 12px;
    line-height: 1.2;
    background: var(--bg);
    color: var(--f);
    -webkit-app-region: drag;
    overflow: hidden;
  }
</style>

<ViewPort />
