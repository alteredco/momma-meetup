<script>
  export let type = "button";
  export let caption;
  export let href = null;
  export let mode = null;
  export let color = null;
</script>

<style>
  button,
  a {
    box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.26);
    font: inherit;
    border: 1px solid #04d6cc;
    background-color: #04d6cc;
    padding: 0.5rem 1rem;
    color: #fff;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
  }

  button:focus {
    outline: none;
  }

  button:hover,
  button:active,
  a:hover,
  a:active {
    background-color: #04d6cc;
    border-color: #04d6cc;
    box-shadow: 1px 1px 8px rgba(77, 51, 51, 0.26);
  }

  button:disabled,
  button:disabled:hover,
  button:disabled:active {
    background-color: #ccc;
    border-color: #ccc;
    color: #959595;
    box-shadow: none;
    cursor: not-allowed;
  }

  .success {
    background: #01a129;
    border-color: #01a129;
  }

  .success:hover,
  .success:active {
    background: #1ac745;
    border-color: #1ac745;
  }

  .outline {
    background: transparent;
    color: #04d6cc;
    box-shadow: none;
  }

  .outline:hover,
  .outline:active {
    background-color: #df75a1;
    color: #fff;
    box-shadow: none;
  }

  .outline:disabled,
  .outline:disabled:hover,
  .outline:disabled:active {
    background: transparent;
    color: #ccc;
  }

  .outline.success {
    border-color: #01a129;
    color: #01a129;
  }

  .outline.success:hover,
  .outline.success:active {
    background: #c2ffd1;
  }
</style>

{#if href}
  <a {href}>
    <slot />
  </a>
{:else}
  <button class="{mode} {color}" {type} on:click>
    <slot />
  </button>
{/if}
