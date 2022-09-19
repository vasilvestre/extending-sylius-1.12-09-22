---
titleTemplate: '%s'
theme: seriph
background: https://source.unsplash.com/1920x1080/?developer
highlighter: shiki
lineNumbers: true
info: false
css: unocss
hideInToc: true 
---
# Étendre Sylius 1.12

Admin, API (Platform)

<div class="abs-br m-6 flex gap-2">
  <a rel='nofollow' href='https://www.qr-code-generator.com' border='0' style='cursor:default'><img src='https://chart.googleapis.com/chart?cht=qr&chl=https%3A%2F%2Fgithub.com%2Fvasilvestre%2Fextending-sylius-1.12-09-22&chs=180x180&choe=UTF-8&chld=L|2' alt=''></a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: center
hideInToc: true
---

# De quoi on parle ?

<Toc />

---
layout: center
class: text-center
title: Présentation
level: 1
src: ./pages/qui_suis_je.md
---

---
layout: center
class: text-center
hideInToc: true
src: ./pages/qui_sommes_nous.md
---

---
layout: section
title: Sylius 1.12
level: 1
---
# Sylius 1.12

---
layout: center
title: Nouveautés annoncées
level: 2
---

<img src="/1.12-release-content.png" width="620" height="501">

---
layout: center
src: ./pages/date_et_contenu.md
---

---
hideInToc: true
layout: section
---
# API Sylius

---
layout: center
hideInToc: true
---

// TODO : document how it's working about APIP 2.7 support has been release and support is done

---
layout: section
title: Contexte projet
level: 1
---

# Contexte projet

## Les marketplace

---
layout: center
title: Tendance
level: 2
---

# Tendance

<img src="/marketplace_stats.png" height="381" width="600">

---
layout: center
src: ./pages/problematiques.md
---

---
layout: section
src: ./pages/sections/exemples.md
---

---
layout: section
src: ./pages/sections/ajout_siret.md
---

---
layout: section
src: ./pages/sections/profil_publique.md
---

---
layout: section
src: ./pages/sections/unicite_produit.md
---

---
hideInToc: true
---

# Mettre du code ici

Use code snippets and get the highlighting directly![^1]

```ts {all|2|1-6|9|all}
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: User) {
  const user = getUser(id)
  const newUser = { ...user, ...update }
  saveUser(id, newUser)
}
```

<arrow v-click="3" x1="400" y1="420" x2="230" y2="330" color="#564" width="3" arrowSize="1" />

[^1]: [Learn More](https://sli.dev/guide/syntax.html#line-highlighting)

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
layout: end
hideInToc: true
---

<!-- Remercier Akawaka, le staff nottament Thibault et Grégoire Hebert -->