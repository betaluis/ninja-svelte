<script>
  let make;
  let model;
  let year;

  let wheelDrive;
  let addOns = [];

  const handleSubmit = () => {
    console.log(year, make, model, addOns, wheelDrive);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="number" placeholder="Year" bind:value={year} />
  <input type="text" bind:value={make} placeholder="Make" />
  <input type="text" bind:value={model} placeholder="Model" />
  <div>
    <label>
      <input type="checkbox" bind:group={addOns} value="A/C" />
      A/C
    </label>
    <label>
      <input type="checkbox" bind:group={addOns} value="Auto Pilot"/>
      Auto Pilot
    </label>
    <label>
      <input type="checkbox" bind:group={addOns} value="Bluetooth"/>
      Bluetooth
    </label>
    <label>
      <input type="checkbox" bind:group={addOns} value="Seat Warmers"/>
      Seat Warmers
    </label>
  </div>
  <select bind:value={wheelDrive}>
    <option value="Front wheel drive">Front Wheel Drive</option>
    <option value="Rear wheel drive">Rear Wheel Drive</option>
  </select>
  <button type="submit">Add Vehicle</button>
</form>

<style>
  form { 
    max-width: 300px;
    margin: 0 auto;
  }
  input[type="text"], input[type="number"], button {
    display: block;
    width: 100%;
    margin: 10px 0;
  }
  form > div {
    margin: 10px 0 10px;
  }
  label {
    text-align: left;
  }
  select {
    display: block;
    margin: 10px 0;
  }
  button {
    background: orangered;
    color: white;
    border-radius: 10px;
    border: none;
    padding: 8px 15px;
    cursor: pointer;
    border: 2px solid transparent;
    margin: 15px auto;
  }
  button:focus {
    border: 2px solid black;
  }
</style>
