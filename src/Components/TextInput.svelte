<script>
  export let controlType;
  export let id;
  export let label;
  export let rows;
  export let value;
  export let type;
</script>

<style>
  .form-control {
    border-color: #e40763;
    outline: none;
  }

  label {
    display: block;
    margin-bottom: 0.5rem;
    width: 100%;
  }

  .form-control {
    padding: 0.5rem 0;
    width: 100%;
    margin: 0.25rem 0;
  }
</style>

<div class="form-control">
  <label for={id}>{label}</label>
  {#if controlType === 'textarea'}
    <textarea {rows} {id} {value} on:input />
  {:else}
    <input {type} {id} {value} on:input />
  {/if}
</div>
