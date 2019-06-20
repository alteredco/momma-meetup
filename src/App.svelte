<script>
  import Header from "./Components/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./Components/TextInput.svelte";
  import Button from "./Components/Button.svelte";

  let title = "";
  let subtitle = "";
  let address = "";
  let email = "";
  let description = "";
  let imageUrl = "";

  let meetups = [
    {
      id: "m1",
      title: "Women Returners",
      subtitle: "Motivational meeting of women returning to work",
      description:
        "In this meetup we will discuss what we have accomplished this past month, what we are looking forward to and the challenges we face.",
      imageUrl:
        "https://images.unsplash.com/photo-1477925181867-37d89ee64b58?ixlib=rb-1.2.1&auto=format&fit=crop&w=1645&q=80",
      address: "234 Returner Road, 32324 Brussels",
      contactEmail: "catchem@test.com"
    },
    {
      id: "m2",
      title: "Bumps and Babies",
      subtitle: "Moms-to-be and Baby Mommas",
      description: "Coffee, chat and all of that!",
      imageUrl:
        "https://images.unsplash.com/photo-1520736179427-d7f281fc39f0?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=668&q=80",
      address: "234 Kiddy Corner, 32322 Brussels",
      contactEmail: "bakeem@test.com"
    },
    {
      id: "m3",
      title: "Parents Can Code",
      subtitle: "Coding Co-working for parents",
      description: "Code, coffee, chat, kids",
      imageUrl:
        "https://images.unsplash.com/photo-1554902748-feaf536fc594?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1650&q=80",
      address: "234 Codery Corner, 32122 Brussels",
      contactEmail: "codeem@test.com"
    }
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address
    };

    meetups = [newMeetup, ...meetups];
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />
<main>

  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      type="text"
      id="title"
      label="Title"
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      type="text"
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      type="text"
      id="img"
      label="Image Url"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      type="text"
      id="address"
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      type="text"
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
    <Button type="submit" caption="Save" />
  </form>

  <MeetupGrid {meetups} />
</main>
