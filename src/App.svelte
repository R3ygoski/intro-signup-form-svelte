<script>
  import Attribution from "./components/Attribution.svelte";
import Form from "./components/Form.svelte";
  
</script>

<main>
  <section class="description_section">
    <h1 class="title">Learn to code by watching others</h1>
    <p class="description">See how experienced developers solve problems in real-time. Watching scripted tutorials is great, but understanding how developers think is invaluable.</p>
  </section>
  <section class="form_section">
    <article class="article">
      <h2 class="article__title">Try it free 7 days <span>then $20/mo. thereafter</span></h2>
    </article>
    <Form/>
  </section>
  <Attribution/>
</main>

<style lang="scss">
  @use './scss/var';
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    padding: 5.5rem 1.5rem 4.25rem 1.5rem;
    .description_section {
      .title {
        text-align: center;
        font-weight: 700;
        font-size: 1.75rem;
        line-height: 2.4rem;
        margin-bottom: 1.3rem;
        color: var.$white;
      } 
      .description {
        text-align: center;
        font-weight: 500;
        color: var.$white;
      }
    }
    .form_section {
      .article {
        background: var.$blue;
        margin-top: 4.3rem;
        padding: 1.15rem 3.5rem;
        height: 88px;
        border-radius: .5rem;
        color: var.$white;
        box-shadow: 0 4px 0px rgba(0,0,0,.2);
  
        min-width: 315px;
        &__title {
          text-align: center;
          display: block;
          font-size: 1rem;
          font-weight: 600;
        }
      }
    }
  }
  @media (min-width: 375px){
    main {
      .form_section {
        .article {
          padding: 1.15rem 4.5rem;
        }
      }
    }
  }
  @media (min-width: 1024px){
    main {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      .description_section {
        width: 40%;
        padding-left: 3rem;
        .title {
          text-align: start;
          font-size: 3rem;
          line-height: 3rem;
        }
        .description {
          text-align: start;
          margin-top: 2.75rem;
        }
      }
      .form_section {
        margin-left: 4.825rem;
        padding-bottom: 4rem;
        .article {
          width: 540px;
          height: 72px;
        }
      }
    }
  }
</style>
