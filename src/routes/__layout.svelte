<script>
  import App from './fb'
  import {onMount} from 'svelte'
  import {getAuth, onAuthStateChanged} from 'firebase/auth'
  import {goto} from '$app/navigation'

  onMount(() => {
    const auth = getAuth();
    onAuthStateChanged(auth, (user) => {
      if(user) {
        console.log('Welcome to the file portal')
      } else {
        goto('/login')
      }
    })
  })
</script>

<slot />