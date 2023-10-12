---
title: CUIB-Mobile
publishDate: 2023-02-10 00:00:00
img: /assets/photos-projets/cuib-mobile.png
img_alt: Page d'accueil de l'application CUIB pour la version mobile
description: |
  Dand la continuité du projet CUIB-Mediatek, j'ai réalisé pour le même client (communauté urbaine du nord) la version mobile de l'application.
tags:
  - Kotlin
  - Gradle
  - Android Studio
---

Dans le cadre de ce projet, j'ai utilisé les technologies suivantes :

<ul>
				<li>Kotlin</li>
				<li>Microsoft SQL Server</li>
				<li>Gradle</li>
				<li>Android Studio</li>
</ul>

> Quelques interfaces utilisateur que j'ai conçu avec Android Studio :

<div style="text-align: center">
<img src="/assets/photos-projets/cuib-mobile-selected.png" alt="interface utilisateur pour voir le detail de l'article choisi" style="width: 65%;  height: 60%" />
</div>

<h6 class="text-center ">interface utilisateur pour voir le detail de l'article choisi</h6>

<div style="text-align: center">
<img src="/assets/photos-projets/cuib-mobile-connexion.png" alt="interface utilisateur pour se connecter"  
style="width: 50%;  height: 60%;" />
</div>

<h6 class="text-center ">interface utilisateur pour se connecter</h6>

> La classe <span class="fw-bold text-primary ">Kotlin</span> "Article" :

Voici un exemple de la classe "Article" qui représente les différents types de média (Film, Livre, Album, single) sous les différents formats : 

<div style="font-weight: bold; padding: 20px; border: 1px solid gray;border-radius:10px;">
data class Article (</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var ean13: String,</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var prixAchat: BigDecimal,</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var titre: String,</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var grandValeur: Boolean,</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var idEditeur: Int,</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var idFormat: Int,</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var idSerie: Int,</br>
       &nbsp;&nbsp;&nbsp;&nbsp;var imageMedia: ImageView</br>
    )</br>
</div>

Pour pouvoir charger tous les articles depuis la base de données et les présenter à l'utilisateur sans ralentir les performances de l'application CUIB-Mobile, j'ai mis en place un RecyclerView.