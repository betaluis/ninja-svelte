<script>
  let family = [
    { name: "Lauren", relationship: "wife", age: 25, id: 1 },
    { name: "Mike", relationship: "brother", age: 21, id: 2 },
    { name: "Katherine", relationship: "sister", age: 18, id: 3 },
    { name: "Ana", relationship: "mom", age: 56, id: 4 },
    { name: "Jose", relationship: "dad", age: 53, id: 5 }
  ]
</script>

<section>

  {#each family as person (person.id)}
    <h2>{person.name}</h2>
    <p>{person.name} is your {person.relationship} and is {person.age} years old.</p>
  {:else}
    <p>There are no members in your family.</p>
  {/each}

</section>

<style></style>
