<script>
   let enteredPassword = '';
   let passwordValidity = 'short'

   let passwords = [];

   $: if(enteredPassword.trim().length < 5){
      passwordValidity = 'short'
   } else if(enteredPassword.trim().length > 10) {
      passwordValidity = 'long'
   } else{
      passwordValidity = 'valid'
   }

   // $: password = console.log(password);

   const checkLength = () => {
      // console.log(e.target.value);
      console.log('text');
   }

   const confirmPassword = () => {
      if(passwordValidity === 'valid'){
         passwords = [...passwords, enteredPassword];
      }
   }

   const removePassword = (index) => {
      passwords = passwords.filter((passwords, idx) => {
         return idx !== index;
      });
   }

</script>

<div class="form-control">
   <label for="password">Password</label>
   <input type="password" bind:value={enteredPassword} id="password" />
</div>

<button on:click={confirmPassword}>Confirm Password</button>

{#if passwordValidity === 'short'}
   <p>Password is too Short</p>
{:else if passwordValidity === 'long'}
   <p>Password is too Long</p>
{:else}
   <p>Password: {enteredPassword}</p>
{/if}

<ul>
   {#each passwords as password, i (password)}
      <li on:click={ () => removePassword(i)}>{password}</li>
   {/each}
</ul>