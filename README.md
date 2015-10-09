Viikkoharjoitus 1: Google App Engine
------------------------------------

Ensimmäisessä harjoituksessa tutustutaan Google App Engineen. Tarkoituksena on saada kehitysympäristö pystytettyä ja luoda pieni Hello World -sovellus. Sovellus voidaan täten suorittaa paikallisesti tai julkaista pilveen.

## Kehitysympäristön asennus

App Engine -sovelluksia luodakseen täytyy olla Google-tili sekä asentaa [Python 2.7.x](https://www.python.org/downloads/) sekä [App Engine SDK for Python](https://cloud.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python). Sovelluksen tiedostoja voi periaatteessa muokata millä tahansa editorilla, ja sitten ajaa SDK:n komentorivityökaluilla. SDK:n mukana tulee ajoympäristö, jossa sovelluksia voi ajaa omalla koneellaan ennen julkaisua App Enginen pilveen.

Käydään tässä läpi kaksi vaihtoehtoista kehitysympäristön asennustapaa.

### Vaihtoehto 1: Asentaminen omalle koneelle

Luultavasti paras vaihtoehto on asentaa [Python 2.7.x](https://www.python.org/downloads/) ja [Google Cloud SDK](https://developers.google.com/cloud/sdk/) omalle koneelle.

Yksi varsin mukava vaihtoehto kehitysympäristöksi on asentaa yllä mainittujen lisäksi [Eclipse](http://www.eclipse.org/downloads/) ja siihen [PyDev-plugin](http://pydev.org/index.html) (asenna Eclipsessä: *Help -> Install New Software -> Work With: http://pydev.org/updates -> PyDev -> ...*). Tällöin saa Python-kehitystä auttavia juttuja ja App Engine -sovelluksia voi ajaa ja julkaista suoraan Eclipsestä käsin.


### Vaihtoehto 2: Lintula

Jos ei jostain syystä halua/voi asentaa kehitysympäristöä omalle koneelle, voi App Engine -sovelluksia tehdä Lintulassakin.

Lintulaan on asennettu App Engine SDK sekä Python 2.7. SDK:n sovellukset sijaitsevat poluissa
`/home/palpo/bin/dev_appserver` ja `/home/palpo/bin/appcfg`.

Voit esimerkiksi lisätä seuraavan rivin ~/.bashrc -tiedostoosi:

    export PATH="$PATH:/home/palpo/bin/"

jolloin sovelluksia voi käyttää esim. näin:

    dev_appserver helloworld

(Jotta PATH-muutos tulee heti voimaan voit komentaa: `source ~/.bashrc` )

#### Porttiforwardointi

Jos käytät Lintulaa SSH-yhteyden yli ja haluat testata palvelua oman koneesi graafisella selaimella joudut turvautumaan porttiforwardointiin. Forwardointi on helppoa tehdä esim. Puttyllä.

1. Puttyn asetuksissa siirry *Connection->SSH->Tunnels* välilehdelle.
2. Kirjoita *Add new forwarded port* -kohtaan sourceksi valitsemasi *PORTTINUMERO* ja destinaatioksi *arokorppi.cs.tut.fi:APPENGINE_PORTTI* ja radiobuttonista local.
3. Nyt voit yhdistää arokorpilla olevaan palveluun omalla koneellasi olevalla selaimella kirjoittamalla selaimen osoitekenttään *http://localhost:PORTTINUMERO/*

Jotta SDK:n ajama sovellus kuuntelee muitakin kuin lokaaleja yhteyksiä, on sitä käynnistettäessä määriteltävä host (0.0.0.0 = kaikki). Porttina voi käyttää vaikka jotain väliltä 40000-50000 joka ei ole kenenkään muun käytössä.

    dev_appserver . --port 40404 --host 0.0.0.0


## Muutama linkki

Voi aloittaa vaikkapa linkistä:

* [Getting started with Python 2.7](https://cloud.google.com/appengine/docs/python/gettingstartedpython27/introduction)

    * [SDK:n](https://cloud.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python) asennuksen jälkeen voi tehdä pienen [Hello World -sovelluksen](https://cloud.google.com/appengine/docs/python/gettingstartedpython27/helloworld).

* App Engine sisältää [webapp2-sovelluskehyksen](https://cloud.google.com/appengine/docs/python/gettingstartedpython27/usingwebapp) ([tarkempi dokumentaatio](https://webapp-improved.appspot.com/)), joka reitittää HTTP-pyynnöt sovellukselle. Muitakin sovelluskehyksiä (mm. [Django](http://www.djangoproject.com/), [Flask](http://flask.pocoo.org/)) voi käyttää. Webapp2 on kuitenkin yksinkertainen, oletuksena mukana App Enginessä ja riittää hyvin mm. harjoitustyön tekoon.

* [App Engine Python-dokumentaatio](https://cloud.google.com/appengine/docs/python/)

* App Engine -sovelluksiaan voi hallinnoida ja tarkkailla [täällä](https://appengine.google.com/) ja/tai [täällä](https://console.developers.google.com/project).


## Tehtävä: luo ja aja App Engine -sovellus

1. Asenna ja konffaa tarvittavat työkalut App Engine -sovellusten tekoon
2. Luo yksinkertainen App Engine -webbisovellus, joka vaikkapa tulostaa tekstin "Moi".
3. Aja sovellus paikallisessa kehitysympäristössä
4. Julkaise sovellus pilveen, niin että se näkyy osoitteessa
<sovelluksen nimi>.appspot.com
