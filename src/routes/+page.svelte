<script>
  import { onMount } from "svelte";
  import { appWindow } from "@tauri-apps/api/window";
  import { onDestroy } from "svelte";

  const fullScreenChange = async () => {
    if (document.fullscreenElement) {
      await appWindow.setFullscreen(true);
    } else {
      await appWindow.setFullscreen(false);
    }
  };

  onMount(() => {
    document.addEventListener("fullscreenchange", fullScreenChange);
  });

  onDestroy(() => {
    document.removeEventListener("fullscreenchange", fullScreenChange);
  });
</script>

<h1>Welcome to SvelteKit</h1>
<p>
  Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
</p>
