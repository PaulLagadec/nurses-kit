<script>
  import { SITE } from "$lib/site.js";
</script>

<svelte:head>
  <title>Secteur d’intervention — Infirmier(ère) à domicile à Lodève</title>
  <meta name="description" content="Secteur d’intervention : Lodève, Lodévois / Larzac et communes alentours. Soins infirmiers exclusivement à domicile, 7j/7." />
</svelte:head>

<div class="container">
  <section class="card">
    <h1>Secteur d’intervention</h1>

    <p>
      Interventions à domicile sur <strong>{SITE.area}</strong>.
      Selon la tournée, nous confirmons rapidement la possibilité d’intervention.
    </p>

    <p>
      Contact : <a href={"tel:" + SITE.phoneTel}>{SITE.phoneDisplay}</a> — <a href={"mailto:" + SITE.email}>{SITE.email}</a>.
    </p>
  </section>
</div>

<style>
.card{
  background: var(--card);
  border: 1px solid rgba(0,0,0,0.06);
  border-radius: 16px;
  padding: 16px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.06);
}
</style>
