<script>
  // Tutorials
  import ReactiveValues from "./tutorial/gettingStarted/ReactiveValues.svelte";
  import Loops from "./tutorial/gettingStarted/Loops.svelte";
  import InlineEventHandlers from "./tutorial/gettingStarted/InlineEventHandlers.svelte";
  import ModalComponent from "./tutorial/gettingStarted/ModalComponent.svelte";
  import SlotsModal from "./tutorial/gettingStarted/SlotsModal.svelte";
  import AddTodo from "./components/AddTodo.svelte";
  import Forms from "./tutorial/gettingStarted/Forms.svelte";
  import TodoModal from "./components/TodoModal.svelte";

  export let name;

  let count = 0;
  const handleClick = () => {
    count = ++count;
  };

  // const handleInput = (e) => {
  // 	count = e.target.value; // This is one way binding.
  // }
  //===================================================//

  let belt = "black";

  let showModal = false;
  let showSlotModal = false;
  let showFormModal = false;

  const toggleModal = () => {
    showModal = !showModal;
  };

  const toggleSlotModal = () => {
    showSlotModal = !showSlotModal;
  };

  const toggleFormModal = () => {
    showFormModal = !showFormModal;
  };

  let vehicles = [];
  const addVehicle = (e) => {
    console.log(e.detail);
    const vehicle = e.detail;
    vehicles = [vehicle, ...vehicles];
  };

  /////////// TODO APP ////////////

  let todos = [];
  let showTodoModal = false;
  const toggleTodoModal = () => {
    showTodoModal = !showTodoModal;
  }
  const addTodo = (e) => {
    const newTodo = e.detail;
    console.log(newTodo)
    todos = [newTodo, ...todos];
    showTodoModal = false;
  }

  const updatedTodoList = (e) => {
    const updatedList = e.detail;
    todos = [...e.detail];
  }
</script>

<main>
  <h1>Hello {name}!</h1>
  <p>
    {count}
  </p>
  <button on:click={handleClick}>Add count</button>
  <!-- <input type="text" on:input={handleInput} value={count}> // one way binding -->
  <input type="text" bind:value={count} />
  <!-- two way binding -->

  <!-- ======================================================================== -->
  <div class="linebreak" />

  <h2>Belt Color</h2>
  <p>Your current belt color is: <span style="color: {belt}">{belt} </span></p>
  <button on:click={() => (belt = "blue")}>Demote to blue</button>
  <input type="text" bind:value={belt} />

  <!-- ======================================================================== -->
  <div class="linebreak" />
  <ReactiveValues />

  <!-- ======================================================================== -->
  <div class="linebreak" />
  <Loops />

  <!-- ======================================================================== -->
  <div class="linebreak" />
  <h2>Inline Event Handlers</h2>
  <InlineEventHandlers />

  <!-- ======================================================================== -->
  <!-- Components / Event Forwarding / Event Modifier -->
  <div class="linebreak" />
  <h2>Component - Modal</h2>
  <ModalComponent
    message="Hey, I am a prop value."
    isPromo={true}
    {showModal}
    on:click={toggleModal}
  />
  <!-- The event modifier only fires the first time that it's clicked. -->
  <button on:click|once={toggleModal}>Open Modal</button>

  <!-- ======================================================================== -->
  <!-- In a real app I wouldn't create a whole new modal to show. I would reuse the one above and change the html content within, but since I want to separate the content shown on the tutorial I created a new modal. -->
  <!-- Slot Modal -->
  <div class="linebreak" />
  <h2>Slots</h2>
  <SlotsModal {showSlotModal} on:click={toggleSlotModal}>
    <AddTodo />
  </SlotsModal>
  <button on:click={toggleSlotModal}>Add Todo</button>
  <p>
    In this section we changed the html inside of the modal by passing in a
    slot.
  </p>

  <!-- ======================================================================== -->
  <div class="linebreak" />
  <h2>Forms</h2>
  <h4>Add your vehicle below</h4>
  <ModalComponent
    message="Add Vehicle"
    isPromo={false}
    showModal={showFormModal}
    on:click={toggleFormModal}
  >
    <Forms />
  </ModalComponent>
  <button on:click={toggleFormModal}>Add Vehicle</button>
  <!-- ======================================================================== -->
  <div class="linebreak" />
  <h2>Dispatching Custom Events</h2>
  <h4>Vehicles:</h4>
  {#if vehicles.length === 0}
    <p style="margin: 20px 0 40px">
      No vehicles listed. Guess you're walking home.
    </p>
  {:else}
    {#each vehicles as vehicle (vehicle.id)}
      <div>
        <p>Year: {vehicle.year}</p>
        <p>Make: {vehicle.make}</p>
        <p>Model: {vehicle.model}</p>
      </div>
    {/each}
  {/if}
  <Forms on:addVehicle={addVehicle} />

  <!-- ======================================================================== -->
  <div class="linebreak" />
  <h2>Create To Do</h2>
  <InlineEventHandlers {todos} on:updatedTodoList={updatedTodoList} />
  <button on:click={toggleTodoModal}>Add To Do</button>
  <TodoModal title="Add Todo" {showTodoModal} on:click={toggleTodoModal}>
    <AddTodo on:addTodo={addTodo} {showTodoModal}/>
  </TodoModal>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
  .linebreak {
    height: 2px;
    width: 100%;
    background-color: #ccc;
    margin: 20px 0;
  }
</style>
