<script>
 import Button from "./Button.svelte";
 import Form from "./Form.svelte";
 import "purecss";
</script>

<style>
  :root {
    --primary: #253854;
    --foreground: #333;
    --background: #eee;
  }

  main {
    font-family: sans-serif;
    text-align: center;
    color: var(--foreground);
    background: var(--background);
    padding: 1rem;
    /* flex-grow: 1; */
  }

  h1 {
    color: var(--primary);
  }

  p {
    margin-top: -1em;
    margin-bottom: 1.5em;
    opacity: 0.5;
  }

  footer {
    margin-top: 1rem;
    opacity: 0;
    /* text-align: right; */
  }

  footer:hover {
    opacity: 1;
  }

  footer a {
    color: #b43c3c;
  }
</style>

<main>
	<h1>Wage ⇌ Income ⇌ Salary Calculator</h1>
  <p>For rough estimations &ndash; expect floating-point errors</p>
	<Form />
  <footer>
    Made by <a href="https://tymek.cz">Tymek.Cz</a>
  </footer>
</main>
