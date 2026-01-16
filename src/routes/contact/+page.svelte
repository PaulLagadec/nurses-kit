<script>
  import { SITE } from "$lib/site.js";
</script>

<svelte:head>
  <title>Contact — Infirmier(ère) à domicile à Lodève</title>
  <meta name="description" content="Contact : téléphone, email et adresse de référence. Soins infirmiers exclusivement à domicile à Lodève et Lodévois / Larzac, 7j/7." />
</svelte:head>

<div class="container">
  <section class="card">
    <h1>Contact</h1>

    <p>
      <strong>Téléphone :</strong> <a href={"tel:" + SITE.phoneTel}>{SITE.phoneDisplay}</a><br />
      <strong>Email :</strong> <a target="_blank" rel="noopener noreferrer"href={"mailto:" + SITE.email}>{SITE.email}</a><br />
      <strong>Disponibilité :</strong> {SITE.availability}<br />
      <strong>Adresse de référence :</strong> {SITE.address}<br />
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
.card-inner{
  margin-top: 16px;
  padding: 14px;
  border-radius: 14px;
  border: 1px solid rgba(0,0,0,0.06);
  background: rgba(57, 89, 127, 0.04);
}
.muted{
  color: rgba(0,0,0,0.70);
}
</style>
