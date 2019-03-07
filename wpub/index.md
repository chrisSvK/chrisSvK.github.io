---
layout: wpub
title: Wpub
---

# Predmet Webové publikovanie

Na tejto stránke budú uverejnené zadania a projekty z predmetu Webové publikovanie.

*****
## Zadanie č. 1 - Osobná webová prezentácia na GitHub pages

Prvé zadanie je tento web vytvorený pomocou statického generátoru 
[Jekyll](https://jekyllrb.com)  a publikovaný na [Github Pages](https://pages.github.com).

Web obsahuje [5 podstránok](https://chrissvk.github.io/sitemap.xml).
Na tvorbu týchto podstránok boli využité možnosti Jekyllu, html, css a jazyku [Liquid](https://shopify.github.io/liquid/)

Každá podstránka má vlastný layout ktorý využíva defaultný layout s hlavičkou a pätou.

Hlavný obsah podstránok sa nachádza v jednotlivých priečinkoch s názvom danej podstránky a umiestnené v príslušnom súbore
index.html 

Všetky štýly sú definované v css/main.css 

Použité premenné : 
- globálne
    * page.content
    * page.title
    * site.time
    * layout
- vlastné
    * age
    * year
    * movies
        * ich ďalšie atribúty
    * shows
        * ich ďalšie atribúty
    * filmyContent
    * hudba-desc
    * youtube
    * spotify
    
Použité tagy:
* capture - pri získaní roku na výpočet veku
* assign - pri vytváraní nového zoznamu 
* for loop - iterovanie v zoznamoch
* include - Google Analytics 

Použité filtre:
* date: "%Y" - filtrovanie site.time
* minus - odčítanie roku narodenia od aktuálneho roku
* markdownify
* sort - zoradenie zoznamu
* reverse - obratenie zoznamu 

Kolekcie a dátové súbory:
* my_collections/_portfolio_collection/ 
    * markdown subory o projektoch na ktorých som pracoval
* YML dáta vo front matters jednotlivých stránok ktoré používam v layoutoch
    * movies, shows, knihy

Použité pluginy:
*   jekyll-sitemap : generuje sitemap stránky
* jekyll-avatar : odkaz na profilový obrázok účtu na GitHube
* jemoji : použitie emotikonov 











