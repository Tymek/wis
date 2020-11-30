<script>
  const ids = ["h", "d", "w", "m", "y"];

  const names = [
    "hourly wage",
    "daily income",
    "weekly salary",
    "monthly salary",
    "income per year"
  ];

  let multipliers = [8, 5, 4, 12];

  let locked = "m";
  let value;

  const formatter = value => value.toFixed(2);

  $: lockedIndex = ids.findIndex(id => id === locked);

  $: values = ids.map((id, index) => {
    if (index === lockedIndex) {
      return value;
    }

    const isSmallerUnit = index < lockedIndex;

    const multipliersArray = isSmallerUnit
      ? multipliers.slice(index, lockedIndex)
      : multipliers.slice(lockedIndex, index);

    const multiplierValue = multipliersArray.reduce(
      (prev, curr) => prev * curr,
      1
    );

    return formatter(
      isSmallerUnit ? value / multiplierValue : value * multiplierValue
    );
  });
</script>

<style>
  table {
    text-align: left;
    margin: 0 auto;
  }

  td,
  th {
    padding: 0.2em 0.5em;
  }

  input {
    text-align: right;
    line-height: 2em;
  }

  .multiplier {
    display: block;
    width: 5em;
    margin-top: -3rem;
  }
</style>

<form>
  <table>
    <thead>
      <tr>
        <th></th>
        <th>Amout</th>
        <th>Description</th>
        <th>Multiplier</th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      {#each ids as id, index}
        <tr>
          <td>
            <input bind:group={locked} type="radio" value={id} disabled />
          </td>
          <td>
            {#if locked === id}
              <input
                bind:value={value}
                type="number"
                step=".01"
                placeholder="0.00"
              />
            {:else}
              <input
                on:focus={() => {
                  locked = id
                  value = values[index]
                }}
                bind:value={values[index]}
                type="number"
                step=".01"
                placeholder="0.00"
              />
            {/if}
          </td>
          <td>
            {names[index]}
          </td>
          <td>
            {#if index !== 0}
              <input
                type="number"
                placeholder="0"
                bind:value={multipliers[index - 1]}
                class="multiplier"
              />
            {/if}
          </td>
          <td>
            {#if index === 2}
              {multipliers[0] * multipliers[1]} h/week
            {/if}
            {#if index === 3}
              {multipliers[0] * multipliers[1] * multipliers[2]} h/month
            {/if}
            {#if index === 4}
              {multipliers[1] * multipliers[2] * multipliers[3]} days/year
            {/if}
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</form>
