<script>
   import Header from './UI/Header.svelte';
   import MeetupItem from './Meetups/MeetupItem.svelte';

   const meetups = [
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
</script>

<style>

</style>

<Header/>

{#each meetups as meetup (meetup.id)}
   <MeetupItem/>
{/each}


