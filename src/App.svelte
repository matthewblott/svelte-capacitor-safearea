<script lang="ts">
  import { Capacitor } from "@capacitor/core";
  import { SafeArea } from "capacitor-plugin-safe-area";

  $: display = false;

  const toggleMessage = () => {
    display = !display;

    const platform = Capacitor.getPlatform();

    console.log(platform);

    SafeArea.getStatusBarHeight().then(({ statusBarHeight }) => {
      console.log(statusBarHeight, "statusbarHeight");
    });

    SafeArea.getSafeAreaInsets().then(({ insets }) => {
      console.log(insets);
    });
  };
</script>

<main>
  <button on:click={toggleMessage}>Toggle Message</button>

  {#if display}
    <h1>Hello World</h1>
  {/if}
</main>

<style>
  main {
    margin-top: 100px;
  }
</style>
