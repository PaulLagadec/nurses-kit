<script>
  import "../app.css";
  import { SITE } from "$lib/site.js";
</script>

<svelte:head>
  <title>Infirmier(ère) à domicile à Lodève — 7j/7</title>
  <meta name="description" content="Infirmier(ère) à domicile à Lodève et Lodévois / Larzac. Prises de sang, pansements, injections, vaccins, soins post-opératoires, perfusions. Disponible 7j/7." />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="author" content={SITE.collaborators} />
  <link rel="icon" href="/favicon.png" type="image/png" />
  <link rel="apple-touch-icon" href="/favicon.png" />
</svelte:head>

<div class="page-wrapper">
  <header class="site-header">
    <div class="container header-inner">
      <div class="brand">
        <a href="/" class="brand-title">{SITE.headerName}</a>
        <p class="collaborators">{SITE.collaborators}</p>
      </div>

      <nav class="nav">
        <a class="nav-btn" href="/services">Soins</a>
        <a class="nav-btn" href="/secteur">Secteur</a>
        <a class="nav-btn" href="/contact">Contact</a>
        <a class="nav-cta" href={"tel:" + SITE.phoneTel}>Appeler {SITE.phoneDisplay}</a>
        <a class="nav-btn" target="_blank" href={"mailto:" + SITE.email + "?subject=Demande%20de%20soins%20%C3%A0%20domicile"}>
  Email
</a>
      </nav>
    </div>
  </header>

  <main class="page-main">
    <slot />
  </main>

  <footer class="site-footer">
    <div class="container footer-inner">
      <div>
        <div style="font-weight:800;">Cabinet infirmier — {SITE.city}</div>
        <div><strong>Adresse :</strong> {SITE.address}</div>
        <div><strong>Disponibilité :</strong> {SITE.availability}</div>
        <div><a href={"mailto:" + SITE.email}>{SITE.email}</a></div>
      </div>
      <div>
        <a href="/mentions-legales">Mentions légales</a>
      </div>
    </div>
  </footer>
</div>

<style>
.page-wrapper{
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.page-main{
  flex: 1;
}

/* Utilitaires */
.container{
  max-width: 960px;
  margin: 0 auto;
  padding: 24px;
}

/* Header/Footer */
.site-header, .site-footer{
  background: var(--brand);
  color: white;
}
.site-header{
  padding: 14px 16px;
}
.site-footer{
  padding: 16px;
  margin-top: 24px;
}
.site-header a, .site-footer a{
  color: white;
  text-decoration: none;
}

/* Brand */
.brand-title{
  font-weight: 800;
}
.collaborators{
  margin: 2px 0 0;
  font-size: 0.95rem;
  color: rgba(255,255,255,0.88);
}

/* Nav */
.header-inner{
  display:flex;
  gap:12px;
  align-items:center;
  justify-content:space-between;
  flex-wrap:wrap;
  padding: 0; /* on évite double padding */
}
.footer-inner{
  display:flex;
  justify-content:space-between;
  gap:16px;
  flex-wrap:wrap;
  padding: 0;
}

.nav{
  display:flex;
  gap:10px;
  align-items:center;
  flex-wrap:wrap;
}
.nav-btn{
  padding: 10px 12px;
  border-radius: 12px;
  background: rgba(255,255,255,0.12);
  border: 1px solid rgba(255,255,255,0.18);
  font-weight: 700;
}
.nav-btn:hover{
  background: rgba(255,255,255,0.18);
}
.nav-cta{
  padding: 10px 12px;
  border-radius: 12px;
  background: var(--accent);
  color: #111 !important;
  font-weight: 800;
  border: 1px solid rgba(0,0,0,0.15);
}
.nav-cta:hover{
  filter: brightness(0.95);
}
</style>
