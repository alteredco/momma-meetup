<script>
  import Header from "./Components/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./Components/TextInput.svelte";
  import Button from "./Components/Button.svelte";
  import EditMeetup from "./Meetups/EditMeetup.svelte";

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
      contactEmail: "catchem@test.com",
      isFavorite: false
    },
    {
      id: "m2",
      title: "Bumps and Babies",
      subtitle: "Moms-to-be and Baby Mommas",
      description: "Coffee, chat and all of that!",
      imageUrl:
        "https://images.unsplash.com/photo-1520736179427-d7f281fc39f0?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=668&q=80",
      address: "234 Kiddy Corner, 32322 Brussels",
      contactEmail: "bakeem@test.com",
      isFavorite: false
    },
    {
      id: "m3",
      title: "Parents Can Code",
      subtitle: "Coding Co-working for parents",
      description: "Code, coffee, chat, kids",
      imageUrl:
        "https://images.unsplash.com/photo-1554902748-feaf536fc594?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1650&q=80",
      address: "234 Codery Corner, 32122 Brussels",
      contactEmail: "codeem@test.com",
      isFavorite: false
    }
  ];

  function addMeetup(event) {
    const newMeetup = {
      id: Math.random().toString(),
      title: event.detail.title,
      subtitle: event.detail.subtitle,
      description: event.detail.description,
      imageUrl: event.detail.imageUrl,
      contactEmail: event.detail.email,
      address: event.detail.address
    };

    meetups = [newMeetup, ...meetups];
    editMode = null;
  }

  function toggleFavorite(event) {
    const id = event.detail;
    const updatedMeetup = { ...meetups.find(m => m.id === id) };
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    const meetupIndex = meetups.findIndex(m => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
  }

  let editMode = null;
</script>

<style>
  main {
    margin-top: 5rem;
  }

  .meetup-controls {
    margin: 1rem;
  }
</style>

<Header />
<main>
  <div class="meetup-controls">
    <Button on:click={() => (editMode = 'add')}>New Meetup</Button>
  </div>
  {#if editMode === 'add'}
    <EditMeetup on:saveEvent={addMeetup} />
  {/if}
  <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>
