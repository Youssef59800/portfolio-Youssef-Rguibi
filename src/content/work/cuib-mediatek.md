---
title: CUIB-Mediatek
publishDate: 2023-12-05 00:00:00
img: /assets/photos-projets/cuib-home.png
img_alt: Page de connection sur le site de l'appli Myprint
description: |
  J'ai conçu et développé pour le compte d'une communauté urbaine dans le Nord de la France, le projet CUIB mettant en place un systéme informatique permettant la gestion de l'ensemble des médiathèques de son territoire qui sont au nombre de 5.(Demo en dessous) 
tags:
  - Conception BDD
  - JavaFX
  - Quarkus
  - Scene Builder
---
>Demo de l'application CUIB-Mediatek

<div>
<video src="/assets/videos/demo-cuib.mp4" width=100% height=100% autoplay loop ></video>
</div>


Dans le cadre de ce projet, j'ai utilisé les technologies suivantes :

<ul>
				<li>JAVA</li>
				<li>JavaFx</li>
				<li>intelliJ IDEA</li>
				<li>SGBD : Microsoft SQL Server</li>
        <li>Quarkus</li>
        <li>Scene-Builder 18</li>
        <li>Jmerise pour la modélisation conceptuelle de données</li>
        <li>intelliJ IDEA</li>
</ul>

> Le projet CUIB a respecté une architecture MVC, qui offre plusieurs avantages parmi lesquelles :

* &nbsp;&nbsp;Facilité pour retrouver les différents modules ou fonctions de votre code</br>
* &nbsp;&nbsp;Débuggage plus rapide</br>
* &nbsp;&nbsp;Gain de temps à la modification ou ajout de nouvelles fonctionnalités</br>
* &nbsp;&nbsp;Confort pour le développement, par vous-même ou un futur collaborateur</br>
* &nbsp;&nbsp;Facile à maintenir, de par sa séparation obligatoire en fichiers et logique</br>
* &nbsp;&nbsp;Le développement peut se faire à plusieurs niveaux en parallèle</br>
* &nbsp;&nbsp;La décorrélation des vues et de la logique permet de tester le code de manière plus simple et efficace</br>
* &nbsp;&nbsp;Possibilité de réutilisation de code dans d’autres applications</br>
* &nbsp;&nbsp;Un gain de temps de maintenance et d’évolution du site</br>
* &nbsp;&nbsp;Favorise la réutilisation du code et la modularité</br>

<div style="text-align: center;margin-bottom: 50px">
<img src="/assets/photos-projets/mvc-cuib.png" alt="structure MVC du projet" />
</div>

> Le modèle conceptuel de données (MCD) :

<img src="/assets/photos-projets/mcd-cuib.png" alt="MCD du projet" />

> Quelques interfaces utilisateur que j'ai réalisé grâce à l'outil Scene-Builder 18 :

<img src="/assets/photos-projets/cuib-ajout-article.png" alt="interface utilisateur pour ajouter un article" />

<h6 class="text-center ">interface utilisateur pour ajouter un article</h6>

<img src="/assets/photos-projets/cuib-modif-article.png" alt="interface utilisateur pour ajouter un article" />

<h6 class="text-center ">interface utilisateur pour modifier un article</h6>

> Exemple d'une requête SQL écrite dans le courant de ce projet pour pouvoir récupèrer tous les articles stockés dans la base de données : 
<div class="fw-bold">
@Override</br>
public ArrayList&lt;Article&gt getAll()</br> 
     {</br>
        ResultSet rs;</br>
        ArrayList&lt;Article&gt liste = new ArrayList<>();</br>
        String statement = "SELECT EAN13, titre, E.id_editeur, E.nom_editeur," +</br>
                           " F.id_format, F.libelle FROM " +</br>
                           "ARTICLE as A join editeur as E on E.id_editeur = A.id_editeur join " +</br>
                           "[format] as F on F.id_format = A.id_format";</br>
        try (PreparedStatement pStmt = this.connexion.prepareStatement(statement)) {</br>
            pStmt.execute();</br>
            rs = pStmt.getResultSet();</br>
            while (rs.next()) {</br>
                Article newArticle = new Article();</br>
                newArticle.setEAN13(rs.getLong(1));</br>
                newArticle.setTitre(rs.getString(2));</br>
                newArticle.setEditeur(new Editeur());</br>
                newArticle.getEditeur().setId(rs.getInt(3));</br>
                newArticle.getEditeur().setNom(rs.getString(4));</br>
                newArticle.setFormat(new Format());</br>
                newArticle.getFormat().setId(rs.getInt(5));</br>
                newArticle.getFormat().setNom(rs.getString(6));</br>
                liste.add(newArticle);</br>
            }</br>
            rs.close();</br>
        } catch (Exception e) {</br>
            e.printStackTrace();</br>
        }</br>
        return liste;</br>
}</br>



</div>


