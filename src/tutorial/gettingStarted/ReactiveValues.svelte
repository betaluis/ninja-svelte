<script>
    let firstName = "Luis";
    let lastName = "Betancourt";

    // use a value that holds the full name instead of outputting them separately.

    $: fullName = `${firstName} ${lastName}`

    // Reactive statements
    $: console.log(fullName); // This is going to change when the value inside of it changes.

    $: {
        if (fullName.length > 10) console.log("Your name is realy long.")
    }
</script>

<section>
    <h2>What is your name?</h2>
    <!-- <p>{firstName} {lastName}</p> -->
    <p>{fullName}</p>
    <input type="text" bind:value={firstName}>
    <input type="text" bind:value={lastName}>
</section>

<style></style>
