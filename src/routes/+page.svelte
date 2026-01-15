<script>
  import { onMount } from "svelte";
  import { SITE, SERVICES } from "$lib/site.js";

  let revealEl;
  let revealed = false;

  onMount(() => {
    const io = new IntersectionObserver(
      ([entry]) => {
        if (entry.isIntersecting) {
          revealed = true;
          io.disconnect();
        }
      },
      {
        threshold: 0,
        rootMargin: "0px 0px -35% 0px"
      }
    );

    if (revealEl) io.observe(revealEl);
    return () => io.disconnect();
  });
</script>

<svelte:head>
  <title>Infirmier(ère) à domicile à Lodève — 7j/7</title>
  <meta name="description" content="Infirmier(ère) à domicile à Lodève et Lodévois / Larzac. Prises de sang, pansements, injections, vaccins, perfusions, soins post-opératoires. Disponible 7j/7." />
</svelte:head>

<section class="hero">
  <div class="hero-overlay">
    <div class="hero-content">
      <div class="hero-card">
      <h1>Infirmier(ère) à domicile à Lodève</h1>
      <p>Cabinet infirmier — Lodévois / Larzac • Soins à domicile 7j/7</p>

      <div class="hero-actions">
        <a class="primary" href={"tel:" + SITE.phoneTel}>Appeler {SITE.phoneDisplay}</a>
        <a class="secondary" href="/contact">Contact</a>
      </div>
    </div>
  </div>
</section>
<a class="scroll-down" href="#infos" aria-label="Faire défiler vers le contenu">
  <span aria-hidden="true">↓</span>
</a>

<div class="container">
  <!-- C’EST ICI QUE VA reveal-grid -->
  <div id="infos" class={`reveal-grid ${revealed ? "is-visible" : ""}`} bind:this={revealEl}>

    <section class="card card-left">
      <h2>Des soins infirmiers à domicile.</h2>
      <p>
        Besoin d’une prise de sang, d’une injection, d’un pansement ou d’un suivi post-opératoire ? Nous intervenons à domicile sur {SITE.area},
        avec une organisation adaptée à votre situation.
      </p>
      <p>
        Les soins techniques (pansements, injections, prises de sang, perfusions, suivi de traitement), ainsi que les soins de nursing, le pilulier
        et l’accompagnement du maintien à domicile des personnes âgées sont assurés selon prescription lorsque nécessaire.
      </p>

      <div class="actions">
        <a class="btn primary" href={"tel:" + SITE.phoneTel}>Appeler {SITE.phoneDisplay}</a>
        <a class="btn" href={"mailto:" + SITE.email}>Envoyer un email</a>
        <a class="btn" href="/contact">Page contact</a>
      </div>
    </section>

    <section class="card card-right">
      <h2>Soins proposés</h2>
      <ul>
        {#each SERVICES as s}
          <li>{s}</li>
        {/each}
      </ul>
      <p class="muted">Adresse de référence : {SITE.address}.</p>
    </section>
  </div>
</div>
<style>
/* Cache vraiment tout le bloc avant déclenchement */
.reveal-grid{
  display: grid;                 /* IMPORTANT */
  grid-template-columns: 1fr;    /* mobile */
  gap: 16px;
  align-items: start;

  opacity: 0;
  transform: translateY(10px);
  transition: opacity 400ms ease, transform 400ms ease;
}

/* Quand visible, le conteneur apparaît */
.reveal-grid.is-visible{
  opacity: 1;
  transform: translateY(0);
}

/* Desktop */
@media (min-width: 860px){
  .reveal-grid{
    grid-template-columns: 1.1fr 0.9fr;
    gap: 18px;
  }
}
.card-left,
.card-right{
  opacity: 0;
  transition: transform 700ms cubic-bezier(.2,.8,.2,1), opacity 700ms ease;
  will-change: transform, opacity;
}

.card-left{ transform: translateX(-60px); }
.card-right{ transform: translateX(60px); }

.reveal-grid.is-visible .card-left,
.reveal-grid.is-visible .card-right{
  opacity: 1;
  transform: translateX(0);
}

/* Les cartes */
.card{
  background: white;
  border: 1px solid rgba(0,0,0,0.06);
  border-radius: 16px;
  padding: 16px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.06);
}

.card h2{
  margin: 0 0 8px;
}

.card p{
  margin: 0 0 10px;
}

.card ul{
  margin: 0;
  padding-left: 18px;
}

/* Boutons */
.actions{
  display:flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 14px;
}

.btn{
  display:inline-block;
  padding: 10px 14px;
  border-radius: 12px;
  text-decoration: none;
  border: 1px solid rgba(57, 89, 127, 0.25);
  background: rgba(57, 89, 127, 0.08);
  color: #1d2d45;
  font-weight: 700;
}

.btn.primary{
  background: #A28F42;
  border-color: rgba(0,0,0,0.12);
  color: #111;
}

.btn:hover{
  filter: brightness(0.98);
}

/* Texte secondaire */
.muted{
  margin: 12px 0 0;
  color: rgba(0,0,0,0.65);
  font-size: 0.95rem;
}
.scroll-down{
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 44px;
  height: 44px;
  margin: -22px auto 18px; /* remonte un peu sur le hero */
  border-radius: 999px;
  background: rgba(255,255,255,0.85);
  border: 1px solid rgba(0,0,0,0.08);
  box-shadow: 0 10px 25px rgba(0,0,0,0.10);
  text-decoration: none;
  color: #39597F;
  font-size: 22px;
  font-weight: 900;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
}

.scroll-down:hover{
  filter: brightness(0.98);
}

.scroll-down span{
  display: inline-block;
  animation: bounce 1.4s infinite;
}

@keyframes bounce{
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(6px); }
}

@media (prefers-reduced-motion: reduce){
  .scroll-down span{ animation: none; }
}
/* Accessibilité : respecter “réduire les animations” */
@media (prefers-reduced-motion: reduce){
  .card-left, .card-right{
    transition: none;
    opacity: 1;
    transform: none;
  }
}

.hero {
  background: url('/images/pas-de-lescalette.jpg') center/cover no-repeat;
  min-height: 65vh;
  display: flex;
  align-items: center;
  position: relative;
  min-height: 75vh;
  
}

/* voile global léger pour lisibilité, mais pas blanc */
.hero::before {
  content: "";
  position: absolute;
  inset: 0;
  background: linear-gradient(
    110deg,
    rgba(57, 89, 127, 0.65),
    rgba(57, 89, 127, 0.20)
  );
}

.hero-overlay {
  position: relative;
  width: 100%;
}

.hero-content {
  max-width: 960px;
  margin: 0 auto;
  padding: 56px 24px;
}

/* carte “glass” */
.hero-card {
  max-width: 720px;
  padding: 22px 22px;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.82);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  box-shadow: 0 14px 40px rgba(0,0,0,0.18);
  border: 1px solid rgba(255,255,255,0.55);
}

.hero h1 {
  margin: 0 0 8px;
  font-size: 2.2rem;
  line-height: 1.15;
}

.hero p {
  margin: 0 0 18px;
  color: #223;
  font-size: 1.05rem;
}

.hero-actions {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.hero-actions a {
  padding: 12px 16px;
  border-radius: 12px;
  text-decoration: none;
  border: 1px solid transparent;
  font-weight: 700;
}

.hero-actions .primary {
  background: #A28F42;
  color: #111;
}

.hero-actions .primary:hover {
  filter: brightness(0.95);
}

.hero-actions .secondary {
  background: rgba(57, 89, 127, 0.12);
  border-color: rgba(57, 89, 127, 0.25);
  color: #1d2d45;
}

.hero-actions .secondary:hover {
  background: rgba(57, 89, 127, 0.18);
}
</style>


