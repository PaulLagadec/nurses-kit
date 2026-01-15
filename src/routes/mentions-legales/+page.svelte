<script>
  import { SITE } from "$lib/site.js";
</script>

<svelte:head>
  <title>Mentions légales — Infirmier(ère) à domicile à Lodève</title>
  <meta name="description" content="Mentions légales du site — cabinet infirmier à Lodève." />
</svelte:head>

<div class="container">
  <section class="card">
    <h1>Mentions légales</h1>

    <p>
      <strong>Titulaires :</strong> Sylvie Almeras, Blaissillia Devic, Sophie Gallez<br />
      <strong>Adresse :</strong> {SITE.address}<br />
      <strong>Email :</strong> <a target="_blank" href={"mailto:" + SITE.email}>{SITE.email}</a><br />
      <strong>Hébergeur :</strong> (à compléter)
    </p>

    <p>
      Ce site a pour objet la présentation de services infirmiers. Aucune donnée de santé n’est collectée via un espace patient.
    </p>
  </section>
</div>
