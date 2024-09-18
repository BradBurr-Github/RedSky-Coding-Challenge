<script>
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();

    let firstName;
    let lastName;
    let email;
    let avatarLink;
    const handleSubmit = () => {
        const user = {
            id: Math.random(),
            firstName,
            lastName,
            email,
            avatarLink
        };
        console.log(user)
        dispatch('createUser', user)
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <p>FIRST NAME</p>
    <input type="text" bind:value={firstName}>
    <input type="text" bind:value={lastName}>
    <input type="text" bind:value={email}>
    <input type="text" bind:value={avatarLink}>
    <button>CREATE</button>
</form>

<style>

</style>