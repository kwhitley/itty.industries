<script>
  import { navlink } from 'svelte-navlink-action'
  import Footer from '~/layout/Footer.svelte'
  import Nav from '~/layout/Nav.svelte'
  import Page from '~/layout/Page.svelte'
  import ForkMe from '~/components/ForkMe.svelte'
  import '~/styles/app.scss'

  // DEFINES IF THE PAGE IS WIDTH-CONSTRAINED
  let constrained = true
  let year = new Date().getFullYear()
</script>

<svelte:head>
  <link rel="icon" type="image/svg" href="/favicon.png">
  <link rel="preconnect" href="https://api.itty.cards" crossorigin>
  <title>itty.industries</title>
  <meta name="description" content="Official site of itty.industries, home of itty open-source projects on NPM." />
  <meta name="robots" content="index, follow, max-snippet:-1, max-image-preview:large, max-video-preview:-1" />
  <html lang="en" />
</svelte:head>

<ForkMe user="kwhitley" repo="itty.industries" />

<main>
  <Nav version horizontal constrained>
    <!-- <a href="/" use:navlink={{ exact: true }}>Home</a>
    <a href="/about" use:navlink={{ exact: true }}>About</a> -->
  </Nav>

  <section class:constrained>
    <Page>
      <slot />
    </Page>
  </section>

  <Footer constrained={constrained}>
    &copy; {year} itty industries, LLC. All rights reserved.
  </Footer>
</main>

<style lang="scss">
  main {
    display: flex;
    flex-flow: column;
    height: 100%;
    overflow: scroll;

    section {
      flex: 1;
      display: flex;
      flex-flow: row wrap;
      justify-content: center;
    }
  }

  small {
    font-size: 0.5em;
    letter-spacing: 0em;
    color: var(--foreground-25);
    top: -0.4rem;
    position: relative;
  }
</style>
