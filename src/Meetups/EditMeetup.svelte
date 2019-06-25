<script>
  import { createEventDispatcher } from "svelte";
  import TextInput from "../Components/TextInput.svelte";
  import Button from "../Components/Button.svelte";

  let title = "";
  let subtitle = "";
  let address = "";
  let email = "";
  let description = "";
  let imageUrl = "";

  const dispatch = createEventDispatcher();

  function submitForm() {
    dispatch("saveEvent", {
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address
    });
  }
</script>

<style>

</style>

<form on:submit|preventDefault={submitForm}>
  <TextInput
    id="title"
    label="Title"
    value={title}
    on:input={event => (title = event.target.value)} />
  <TextInput
    id="subtitle"
    label="Subtitle"
    value={subtitle}
    on:input={event => (subtitle = event.target.value)} />
  <TextInput
    id="img"
    label="Image Url"
    value={imageUrl}
    on:input={event => (imageUrl = event.target.value)} />
  <TextInput
    id="address"
    label="Address"
    value={address}
    on:input={event => (address = event.target.value)} />
  <TextInput
    id="contact"
    label="Contact Email"
    value={email}
    on:input={event => (email = event.target.value)} />
  <TextInput
    controlType="textarea"
    id="desc"
    label="Description"
    rows="3"
    value={description}
    on:input={event => (description = event.target.value)} />
  <Button type="submit">Save</Button>
</form>
