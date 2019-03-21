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

***

## Zadanie č. 2 - Transformácia vybraného dokumentu do formátu DocBook

Cieľom druhého zadania bolo pretransformovať ľubovolnú prácu v pôvodnom formáte (LaTeX, Word) ,
do formátu [DocBook](https://docbook.org) a následne vygenerovať finálny .pdf súbor.
Na prácu sme využili šablónu pre bakalársku prácu od Jiřího Koska. 
Výsledný dokument má 23 strán z toho obsah práce tvorí cca 13 strán. 

Použité konštrukcie DocBooku: 

Členenie textu: 
* dve kapitoly `<chapter>` , 2 úrovne podkapitol `<section>`
* príloha na konci práce `<appendix>` 
* generovaný obsah
     
Zvýraznenie slov:
* kurzíva `<emphasis>`
* tučné písmo `<emphasis role="strong">` 
* inicialy `<acronym>` 
* premennej kódu programu `<prompt>`
* časti kódu `<programlisting>`
* členenie textu odrážkami `<itemizedlist mark="opencircle">`
* členenie textu číslovaním `<orderedlist>`
    
Odkazy:
* odkazy na iné časti dokumentu, označenie sekcie napr. `<section id="json">` a odkaz na ňu `<link linkend="json">`
    * použité na sekcie HTML, Json, Xpath 
*  URL odkazy `<ulink url="https://introjs.com/">`
    * použité ne weby introjs.com a Hopscotch
        
Poznámky pod čiarou:
* `<footnote>` , poznámka s URL odkamzi na weby introjs.com a Hopscotch pri obrázkoch
    
Vloženie obrázku a tabuliek:
* 7 obrázkov , príklad dole, poprípade doplnený o zmenu rozmeru `contentwidth="781"` v atribúte `<imagedata>`
 ```xml
           <figure id="Obr5">
                      <title>Príklad URL adresy</title>
                      <mediaobject>
                          <imageobject>
                              <imagedata fileref="img/url.JPG"/>
                          </imageobject>
                      </mediaobject>
            </figure>
```
* tabuľka
```xml
            <table frame="all">
                <title/>
                <tgroup>
                    <colspec colname="c1"/>
                    <thead>
                        <row>
                            <entry align="center"/>
                        </row>
                    </thead>
                    <tbody>
                        <row>
                            <entry/>
                        </row>
                    </tbody>
                </tgroup>
            </table>
 ```   
* odkazy na obrázky a tabuľky cez `<link>` , podobne ako odkazy na časti dokumentu , zoznam obrázkov vygenerovaný na začiatku práce za obsahom

Vytvorenie registra pojmov (indexu)

* Vygenerovanie na konci dokumentu cez `<index>` , v texte označené pojmy cez `<indexterm>` s troma úrovňami `<primary>`
 `<secondary>` `<tertiary>` ,  16 pojmov 
 
* Zoznam použitej literatúry

 
 











