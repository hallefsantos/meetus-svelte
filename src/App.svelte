<script>
   import Header from './UI/Header.svelte';
   import TextInput from './UI/TextInput.svelte';
   import MeetupGrid from './Meetups/MeetupGrid.svelte';

   let meetups = [
      {
         id: 'm1',
         title: 'Coding Bootcamp',
         subtitle: 'Learn to code in 2 hours',
         description: 'In this meetup, we will have some experts that teach you how to code',
         imageUrl: 'https://imagens.viajonarios.com.br/2015/09/thumb_DSC07027_1024-1.jpg',
         address: '17th Nerd Road, 32523 New York',
         contactEmail: 'code@teste.com'
      },
      {
         id: 'm2',
         title: 'Swim Togheter',
         subtitle: 'Let\'s go for some swimming',
         description: 'We will simply swim some rounds',
         imageUrl: 'https://d3laewezlz9ul2.cloudfront.net/wp-content/uploads/2017/10/10165849/10252-andy-potts-kona-swim-tips-700x394.jpg',
         address: '30th Times Square, 32523 Miami',
         contactEmail: 'swim@teste.com'
      },
   ]

   let title = '';
   let subtitle = '';
   let address = '';
   let email = '';
   let imageURL = '';
   let description = '';

   const addMeetup = () => {
      const newMeetup = {
         id: Math.random().toString(),
         title,
         subtitle,
         description,
         imageUrl: imageURL,
         address,
         contactEmail: email
      };

      meetups = [newMeetup, ...meetups];
   }
</script>

<style>
   main{
      margin-top: 4rem;
   }

   form {
      width: 30rem;
      max-width: 90%;
      margin: auto;
   }
</style>

<Header/>

<main>
   <form on:submit|preventDefault={addMeetup}>
      <TextInput id="title" type="text" label="Title" value={title} on:input={e => title = e.target.value}/>
      
      <TextInput id="subtitle" type="text" label="Subtitle" value={subtitle} on:input={e => subtitle = e.target.value}/>

      <TextInput id="address" type="text" label="Address" value={address} on:input={e => address = e.target.value}/>

      <TextInput id="imageURL" type="text" label="Image URL" value={imageURL} on:input={e => imageURL = e.target.value}/>

      <TextInput id="email" type="email" label="E-mail" value={email} on:input={e => email = e.target.value}/>
      
      <TextInput id="description" controlType="textarea" rows="5" label="Description" value={description} on:input={e => description = e.target.value}/>

      <button type="submit">Submit</button>
   </form>

   <MeetupGrid {meetups} />
</main>