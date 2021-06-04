<script>
  import Button from "./Button.svelte";
  import Form from "./Form.svelte";
  import "purecss";
</script>

<style>
  :root {
    --primary: #253854;
    --foreground: #333;
    --background: #f8f8f8;
  }

  :global(body) {
    background: #efefef;
  }

  main {
    font-family: sans-serif;
    text-align: center;
    color: var(--foreground);
    background: white;
    padding: 1rem;
    box-shadow: 0px 5px 9px -4px rgba(0, 0, 0, 0.67);
    border: 1px solid white;
    background: var(--background);
    border-radius: 3px;
  }

  h1 {
    color: var(--primary);
  }

  p {
    margin-top: -1em;
    opacity: 0.5;
  }

  footer {
    margin-bottom: 1.5rem;
  }

  footer a {
    color: #b43c3c;
  }

  .github {
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
  }
</style>

<main>
  <h1>Wage ⇌ Income ⇌ Salary Calculator</h1>
  <p>For rough estimations &ndash; expect floating-point errors</p>
  <footer>
    <a href="https://github.com/Tymek/wis">
      <img src="/github.svg" alt="GitHub" class="github" />
      github.com/Tymek/wis
    </a>
  </footer>
  <Form />
</main>
