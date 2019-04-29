---
layout: wpub
title: Wpub
---

# Predmet Webové publikovanie

Na tejto stránke budú uverejnené zadania a projekty z predmetu Webové publikovanie.

[Zadanie 1](#zadanie-č-1---osobná-webová-prezentácia-na-github-pages) |
[Zadanie 2](#zadanie-č-2---transformácia-vybraného-dokumentu-do-formátu-docbook) |
[Zadanie 3](#zadanie-č-3---xml-prezentácia)

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
    
Vloženie obrázkov a tabuliek:
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
 
Zoznam použitej literatúry
* Odkaz cet `<xref linkend=""/>` , biliografia sa vygeneruje cez  `<bibliography>` , `<surname>`, `<firstname>`, `<title>`,  `<pubdate>`, `<publishername>`, 
`<bibliomisc>`


Úprava XSLT šablóny:

Generovanie zoznamu obrázkov:
*   úprava thesis.xsl, pridanie figure
```xml
    <xsl:param name="generate.toc">
        book title,toc,figure
    </xsl:param>
```

Úprava nadpisu fakulty na titulnej strane 
* úpravou thesis-tp-fo.xsl , pridaním do book.titlepage.before.recto, hyphenate="false"

***

## Zadanie č. 3 - XML prezentácia
 
 Riešením tohto zadanie bolo vytvorenie prezentácie na ľubovolnú tému vo formáte XML. 
 Následne bolo potrebné navrhnúť XSLT šablóny na konverziu prezentácie do formátu XHTML+CSS a súboru PDF.
 
 Vytvorené cieľové súbory sa transformujú pomocou priložených .bat súborov, ktoré na transformáciu využívajú procesory SAXON a XEP.
 
 <br>

 
 **Typ dokumentu a definovanie prezentácie:**
 
 Dokument je písaný v jazyku XML a je bližšie definovaný použitím DTD.
 Základný koreňový element je _slideshow_ ,ktorý predstavuje celú prezentáciu.
 
 Atribútmi prezentácie sú názov témy, autor a farba nadpisov a textov.
 
 Prezentácia môže obsahovať _background-image_,ktorý sa využíva ako obal na úvodný slide. Ďalej je element prezentácie zložený 
 elementmi _slide_ ,ktoré predstavujú už jednotlivé stránky prezentácie.
 
 Jednotlivé stránky prezentácie obsahujú nadpis _title_ a obsah _container_.
 
 V atribútoch slideu je nastavené ID stránky a farba pozadia. 
 
 _Container_ obsahuje texty v elementoch _odstavec_ , obrázky _image_ alebo odkaz na youtube video v elemetne _video_.
 
 Ďalej môže byť _container_ rozdelený na dve polovice _lava-strana_ a _prava-strana_.
 
 V týchto dvoch častiach sa taktiež objavuje _odstavec_ , _image_ aj _video_ , podobne ako v _containeri_.
 
 _Odstavec_ obsahuje samotný text stránky, čiže hlavný obsah.
 
 _Image_ tvorí relatívnu cestu k obrázku danej stránky
 
 _Video_ je odkaz na Youtube video.  
 
 <br>
 
 
 **Transformácia na XHTML:**
 
 XSL transformácia  využíva 9 templates. _Slideshow_, _slide_, _//slide/title_,
 _//slide/container_ , _//slide/container/lava-strana_ , _//slide/container/prava-strana_
 , _odstavec_, _image_ a _video_.  
 
 Hlavná stránka sa vygeneruje pomocou **xsl:result-document**  ako _prezentacia.xhtml_, obsahuje nadpis, autora a pozadie z elementu
 _slideshow_. Taktiež obsahuje tlačidlo s odkazom na prvý slide, ktorý je vygenerovaný v samostatnom
 xhtml súbore.
 
 Slide využíva template _slide_ ktorý taktiež vďaka **xsl:result-document** vygeneruje 
 každý slide na základe jeho unikátneho ID do samostantého suboru _file_id.xhtml_.
 
 Každá vygenerovaná stránka má tagy - html, head, title, body. Štýl je definovaným 
 externým [Bootstrapom](https://getbootstrap.com)  a vlastným _style.css_ súborom kde sú upravené niektoré elementy
 väčšinou práve tie  vygenerované bootstrapom.
 
 Tag body má nastavenú farbu pozadia podľa atribútu v xml v elemente slide. V body sa nachádza
 div element _container_, ktorý slúži ako priestor práve pre obsah containeru z XMLka. 
 Zobrazuje sa tu teda text, obrázky a video. Taktiež je tu pridané stránkovanie (pagination).
 Na vygenerovanie stránkovania bol použitý **xsl:for-each** spolu s podmienkou
 **xsl:choose** - **xsl:when** - **xsl:otherwise** alebo **xsl:if** , ktoré zabezpečujú že sa strákovaním 
 bude možné preklikávať cez existujúce stránky a nevyjde sa z rozsahu. 
 
 Štýly pre jednotlivé html elementy sa pridávajú pomocou **xsl:attribute** a následne poprípade
 **xsl:value-of** vďaka čomu získame údaje z XML súboru. Týmto je dosiahnutá parametrizácia. 
 Využíva sa to pri nastavení farby textu , nadpisov, pozadia. 
 
 Template _video_ vytvára Youtube element iframe s linkom na video z XML súboru. 
 
 <br>
 
 
 **Transformácia na PDF**
 
 Transformácia využíva dva typy **fo:simple-page-master** , _cover_ prvú hlavnú úvodnú stránku 
  a _landscape_ pre zvyšné strany. Rozlíšenie je nastavené na 1000x680 px , _cover_ obsahuje 
  background-image, _landscape_ background-color 
 
 Stránky sa bližšie definujú cez **fo:page-sequence** a **fo:flow** , následne každý element
 z XML je obalený v **fo:block** , využívajú sa presne tie isté template ako pri generovaní 
 XHTML. S rozdielom že miesto HTML elementov sa používa práve **fo:block**, ktorému sa 
 nastavujú špecifické štýly na umiestnenie, veľkosť textu, farbu, zarovnanie apod. 
 
 PDF nepodporuje iframe preto sú videá umiestené v dokumente iba ako linky. 











