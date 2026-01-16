<script>
  import { SITE, SERVICES } from "$lib/site.js";
</script>

<svelte:head>
  <title>Soins infirmiers à domicile — Lodève | {SITE.area}</title>
  <meta name="description" content="Soins infirmiers à domicile à Lodève et Lodévois / Larzac : prises de sang, pansements, injections, vaccins, perfusions, soins post-opératoires, nursing, pilulier." />
</svelte:head>

<div class="container">
  <section class="card">
    <h1>Soins infirmiers</h1>

    <p>
      Nous proposons une gamme complète de soins infirmiers sur
      <strong>{SITE.area}</strong> :
    </p>

    <ul>
      {#each SERVICES as s}
        <li>{s}</li>
      {/each}
    </ul>

    <p class="muted" style="margin-top:16px;">
      Pour une demande : <a href={"tel:" + SITE.phoneTel}>{SITE.phoneDisplay}</a> — <a href={"mailto:" + SITE.email}>{SITE.email}</a>.
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
.muted{
  color: rgba(0,0,0,0.70);
}
</style>
