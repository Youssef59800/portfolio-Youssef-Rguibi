---
title: Myprint
publishDate: 2022-12-15 00:00:00
img: /assets/photos-projets/home-myprint.png
img_alt: page de connection et d'inscription de l'appli Myprint
description: |
  J’ai collaboré à la création et à la réalisation du projet MyPrint. Ce projet consistait en la création d’une application Web permettant l’impression en ligne d’un rapport de stage, thèse, catalogue, flyers…. Et avoir la possibilité soit de se faire livrer à l’adresse souhaitée ou bien faire un retrait directement chez l’imprimeur.(Demo de l'appli en bas de page)
tags:
  - Spring boot
  - Spring
  - Maven
  - Angular
---

Pour la réalisation de ce projet, on a utilisé spring Boot qui est un Framework de développement JAVA pour générer un projet avec tous les CRUD et aussi pour assurer la sécurité de l’application. Le choix de système de base de données s’est porté sur PostgreSQL. Finalement, pour la partie Front-end le choix de l’équipe en concertation avec le client s’est porté sur le Framework Angular.

Les différentes technologies utilisées sont les suivantes :

<ul>
				<li>JAVA</li>
				<li>Spring</li>
				<li>Spring boot</li>
				<li>SGBD : PostreSQL</li>
        <li>Angular</li>
        <li>Typescript</li>
        <li>Bootstrap</li>
        <li>intelliJ IDEA</li>
</ul>

> Développement Back-end : 

Pour configurer Spring Boot et <span class="fw-bold text-primary ">Spring Security</span> avec <span class="fw-bold text-primary ">JSON Web Token</span> (JWT), on a procédé de la manière suivante :

1.	Dans le fichier pom.xml (<span class="fw-bold text-primary ">Maven</span>), on a ajouté les dépendances nécessaires pour Spring Security et JWT : 

<img src="/assets/photos-projets/myprint-pom.png" alt="pom.xml du projet Myprint" />

Dans la classe WebSecurityConfig on a défini la fonction SecurityFilterChain () et on l’a annoté avec l’annotation @Bean.  En résumé SecurityFilterChain () est une interface de Spring Security qui permet de configurer une séquence de filtres de sécurité pour gérer les opérations de sécurité dans notre application. Il offre une flexibilité et un contrôle précis sur la façon dont les filtres sont appliqués aux requêtes HTTP et permet de personnaliser les mesures de sécurité en fonction de nos besoins. On a ainsi autorisé certains chemins sans authentification comme par exemple : la page d’accueil ainsi que la page de connexion et d’inscription. Et pour d’autres chemins on a exigé une authentification comme pour la page de paiement ou pour accéder au tableau de bord (Dashboard) et ce grâce à des rôles.

Le résultat de cette configuration est la suivante :

<div style="font-weight: bold; padding: 20px; border: 1px solid gray;border-radius:10px">
@Bean</br>
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {</br>
        http</br>
                .csrf()</br>
                .disable()</br>
                .authorizeHttpRequests()</br>
                .requestMatchers(UNSECURED_URL)</br>
                .permitAll()</br>
                .and()</br>
                .authorizeHttpRequests()</br>
                .requestMatchers(SECURED_URL_USER)</br>
                .hasAnyAuthority("USER","STAFF","ADMIN")</br>
                .and()</br>
                .authorizeHttpRequests()</br>
                .requestMatchers(SECURED_URL_STAFF)</br>
                .hasAnyAuthority("STAFF","ADMIN")</br>
                .and()</br>
                .authorizeHttpRequests()</br>
                .requestMatchers(SECURED_URL_ADMIN)</br>
                .hasAnyAuthority("ADMIN")</br>
                .anyRequest()</br>
                .authenticated()</br>
                .and()</br>
                .sessionManagement()</br>
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS)</br>
                .and()</br>
                .authenticationProvider(authenticationProvider)</br>
                .addFilterBefore(jwtAuthFilter, UsernamePasswordAuthenticationFilter.class)</br>
                .cors();</br>
        return http.build();</br>
    }</br>
</div>

> Développement Front-end : 

Pour développer la partie Front-end de notre application et en accord avec le client, le choix s’est porté sur le Framework Angular.

Le choix d’utiliser Angular comme Framework pour développer le Front-end de notre application a été motivé par plusieurs facteurs. Voici quelques raisons courantes qui ont influencé ce choix :

1.	Architecture orientée composants : Angular adopte une architecture orientée composants, ce qui facilite la structuration modulaire de l'application. Les composants d'Angular sont réutilisables et indépendants, ce qui permet de développer des interfaces utilisateur modulaires et faciles à maintenir.

2.	Support d’un langage de programmation fortement typé : Angular utilise TypeScript comme langage de programmation par défaut. TypeScript est un sur-ensemble de JavaScript qui offre des fonctionnalités supplémentaires telles que la vérification statique des types, ce qui peut contribuer à la fiabilité et à la maintenabilité du code.

3.	Large écosystème et communauté active :  Angular bénéficie d'une communauté de développeurs active et d'un écosystème riche en bibliothèques, modules complémentaires et outils. Cela facilite la recherche de solutions, l'apprentissage et l'intégration de fonctionnalités supplémentaires dans l’application.

4.	Prise en charge de l'approche de développement SPA : Angular est particulièrement adapté au développement d'applications de type "Single-Page Applications" (SPA). Les SPAs offrent une expérience utilisateur fluide en évitant les rechargements de page fréquents, ce qui peut améliorer les performances et l'ergonomie de l’application.


> Arborescence du projet avec <span class="fw-bold text-danger">Angular</span> :

<img src="/assets/photos-projets/arbo-myprint.png" alt="Arborescence du projet Myprint avec Angular" />

> Demo de l'application Myprint : 

<div>
     <video src="/assets/videos/demo-myprint.mp4" width=100% height=100% autoplay loop ></video>
</div>



