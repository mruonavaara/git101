# Git 101 ![git-logo](images/Git-logo.png)
Git-opas Haaga-Helian opiskelijoille.<br>
Auttaa alkuun Gitin käytön kanssa!

Sisällysluettelo
1. [Mikä on Git ja mihin sitä tarvitaan?](#1-mikä-git-on-ja-mihin-sitä-tarvitaan)
2. [Git:n asennus](#2-gitn-asennus)
3. [Komentorivin käyttö](#3-komentotulkin-käyttö)
4. [Yleisimpiä git-komentoja](#4-yleisimpiä-git-komentoja)
5. [Muita git komentoja](#5-muita-git-komentoja)
6. [Ensimmäisen repositoryn luonti omalle koneelle](#6ensimmäisen-repositoryn-luonti-omalle-koneelle)
7. [Miten viedä muutokset omasta repositorystä etärepositoryyn](#7-miten-viedä-muutokset-omasta-repositorystä-etärepositoryyn)
8. [Haarat ja miksi niitä tarvitaan](#8-haarat-ja-miksi-niitä-tarvitaan)
9. [Merge conflict! Mitä tapahtui, mitä teen?](#9-merge-conflict-mitä-tapahtui-mitä-teen)
10. [Muita huomoita](#10-muita-huomioita)
11. [Mikä ihmeen Github?](#11-mikä-ihmeen-Github)


### 1. Mikä Git on ja mihin sitä tarvitaan?
Git on versionhallintajärjestelmä. Versionhallinnalla tarkoitetaan palvelua, joka säilyttää koodia, eli toisin sanoen varmuuskopioi sitä. Versionhallinnan avulla voidaan muutosten tekemisen jälkeenkin palata aiempiin versioihin, jos esim. jotain menee pieleen. Koodin lisäksi versionhallinnan avulla tehdyt muutokset on helppo dokumentoida. Git on ilmainen ja hajautettu, eli siinä ei ole minkäänlaista keskitettyä palvelinta. Jokainen Git-tietovarasto on itsenäinen.

### 2. Git:n asennus
Git:n käyttämiseksi Git-ohjelmiston on oltava asennettuna tietokoneella, jolla sitä halutaan käyttää. Git-ohjelmiston asentamiseen löytyy useita eri ohjeita. Alla Git:n omat ohjeet.

[Git lataus](https://git-scm.com/downloads)<br>
[Git asennusohjeet](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

#### 2.1 Konfigurointi
Jotta Git:in käyttö olisi mahdollisimman helppoa ja tehokasta, se kannattaa konfiguroida käyttämään tietynlaisia asetuksia ja työkaluja. Konfiguroinnin avulla Git saadaan toimimaan sillä tavalla kuin itse, tai projektitiimi haluaa. 

Konfigurointikomentoja löytyy lukusia, jotka kaikki löytyy komennolla:

- `git config`

##### 2.1.1 Käyttäjätiedot
Jokaiseen versionhallintaan talletettavaan muutokseen tallennetaan sen tehneen käyttäjän nimi ja sähköpostiosoite. Git-ohjelmiston asentamisen jälkeen olisikin hyvä asettaa käyttäjätiedot komennoilla:

- `git config --global user.name "<username>"`
- `git config --global user.email "<email>"`

`<username>` ja `<email>` kohdat korvataan omalla nimellä ja sähköpostilla. Käyttäjätiedot tarvitsee asettaa vain kerran tietokoneelle. --global -tarkentimella tiedot asetetaan siten, että asetukset ovat tietokoneen käyttäjäkohtaiset. Halutessaan voi myös tallentaa käyttäjätietoihin tässä oletus-editorin konfliktien ratkomista varten. Tätä komentoa käyttäen editori avautuu automaattisesti, kun mergessä on konflikti:

- `git config --global core.editor "<editor> --wait"`

##### 2.1.2 Tekstieditori
Git-ohjelmistoa käyttäessä tulee esiin tilanteita, joissa on tarve käyttää tekstieditoria. Ohjelmiston asentamisen jälkeen oletusarvoinen tekstieditori on [Vi](https://fi.wikipedia.org/wiki/Vi). Vi:n käyttäminen voi tuntua haastavalta (ohjeita tosin löytyy esim [täältä](https://fi.wikipedia.org/wiki/Vi#Peruskomennot)), joten Git-ohjelmistossa on mahdollista vaihtaa tekstieditoria komennolla:
- `git config --global core.editor "<editor-and-options>"`

Tekstieditoriksi voi yrittää asettaa varmaan minkä tahansa ohjelman. Perusteelliset ohjeet eri editorien asettamiseksi löytyy [täältä](https://git-scm.com/book/tr/v2/Appendix-C%3A-Git-Commands-Setup-and-Config#_core_editor).

### 3. Komentorivin käyttö
Komentorivi tai komentoliittymä on tapa kommunikoida tietokoneen kanssa. Komentoliittymässä ajetaan tyypillisesti komentotulkkia. Tällöin käyttäjä kirjoittaa komentoriville käynnistettävän ohjelman nimen tai komentotulkin sisäisen komennon mahdollisine parametreineen ja painaa syöttöpainiketta, jolloin komentotulkki käsittelee käskyn ja tulostaa vastineen näytölle.

Komentotulkkeja on [useita](https://en.wikipedia.org/wiki/List_of_command-line_interpreters) ja on tärkeää huomata, etteivät kaikki komennot toimi kaikissa tulkeissa. Ehkä tärkeintä on tietää, että Unixin kaltaisissa käyttöjärjestelmissä (Linux, Mac) on yleensä eri tulkki kuin Windows -käyttöjärjestelmissä. On kuitenkin hyvä huomata, että esimerkiksi [git for windows](https://gitforwindows.org/) asennuksen yhteydessä asennetaan Bash-emulaattori, jossa käytetään Unix-shell -komentoja.

Komentoliittymän käyttö ei välttämättä vaadi suurta järjestelmän tuntemusta, sillä komennot ovat usein lyhennyksiä selväkielisistä englanninkielisistä sanoista, ja niille on yleensä saatavilla käytönaikainen ohje komennoilla help tai man. Komennot annetaan komentoriville muodossa:

    command param1 param2 param3 … paramN

jossa:
- command = annettava komento
- param 1, param2, jne = komennon vaihtoehdot (options) ja argumentit

Komennon vaihtoehtoina (options) voidaan esimerkiksi antaa tarkennuksia, miten komento suoritetaan ja argumentteina esimerkiksi mille tiedostolle komento suoritetaan.

Yleensä kaikki git-komennot annetaankin komentoriviä käyttäen. Komennolla `git help` saadaan lista komennoista, jotka voidaan suorittaa.

Komentorivin komennoista ja käytöstä löytyy internetistä varmasti miljoonia ohjeita, [ihan](http://appro.mit.jyu.fi/itkp1011/luennot/cli/) [suomeksikin](http://users.jyu.fi/~nieminen/ohj1/materiaalia/tyokaluohjeet/komentorivi_selviytyminen.html). Tärkeintä on ehkä ymmärtää, että komentorivia käyttäessä työskennellään aina jossain työhakemistossa (ts working directory tai kansio). Kaikki annetut komennot suoritetaan tässä työhakemistossa ellei toisin komenneta. Esimerkiksi komennon `git init` suorittaminen luo paikallisen tyhjän repositorion sen hetkiseen __työhakemistoon__.

Nykyisen työhakemiston saa selville shell-tulkissa komennolla `pwd` - **p**rint **w**orking **d**irectory. Komento toimii myös Windowsin PowerShellissä, mutta ei command promptissa (cmd).

Työhakemistossa olevat tiedostot ja alihakemistot saa selville suorittamalla komennon `ls` (ei toimi command promptissa, ks [`dir`](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/dir)). `ls` -komennon voi suorittaa myös esimerkiksi vaihtoehdolla (option) `-a`, jolloin listataan myös tiedostot ja kansiot, jotka alkavat `.` merkillä ('piilotetut tiedostot/kansiot'). Esimerkiksi `git init` -komennolla luodaan `.git` hakemisto, joka ei näy pelkällä `ls` -komennolla, mutta näkyy suorittamalla `ls -a`. Komentoa voi myös käyttää antamalla sille argumenttina hakemisto, jonka tiedostot halutaan listata. Esimerkiksi suorittamalla `ls -a /c` -komento, saadaan listattua __kaikki__ tiedosto ja hakemistot, jotka sijaitsevat `/c` -hakemistossa (ts c-asema).

Nykyistä työhakemistoa vaihdetaan komennolla `cd` - ***c***hange ***d***irectory. Komento toimii sekä command promptissa että shellissä. Ilman argumentteja annettaessa Unix-ympäristössä (Linux & Mac) komennon suorittaminen vaihtaa työhakemistoksi käyttäjän kotihakemiston ja Windows-ympäristössä tulostetaan sen hetkinen työhakemisto. Yleensä komennolle kuitenkin annetaan argumenttina se hakemisto, jonka halutaan olevan uusi työhakemisto. Argumentin hakemisto voidaan antaa joko täydellisenä polkuna (absolute path) tai suhteellisena polkuna (relative path). Esimerkiksi, jos työhakemistoksi halutaan vaihtaa `C:\Users\Git-user\Documents`, voidaan käyttää ___mistä tahansa___ työhakemistosta komentoa: `cd /C/Users/Git-user/Documents` (__shell__) TAI jos nykyinen työhakemisto on `C:\Users\Git-user` antamalla komento: `cd Documents`.

### 4. Yleisimpiä git-komentoja

- `git config --global user.name <username>` - Asettaa käyttäjälle nimen, joka näkyy käyttäjän tekemissä commiteissa.

- `git config --global user.email <email>` - Asettaa käyttäjälle sähköpostin, joka näkyy käyttäjän tekemissä commiteissa.

- `git init` - Luo paikallisen tyhjän repositoryn

- `git add .` - Vertaa hakemistoa local repoon ja siirtää kaikki muutokset tilaan staged, eli nyt ne ovat valmiita commitoitavaksi local repoon. Koskee myös tiedoston luomisia ja poistamisia.

- `git commit` - Tallettaa staged tilassa olevat tiedostot local repositoryyn.

- `git commit --amend` - Tällä voit lisätä edelliseen committiin muutoksia, jotka unohdit tehdä (ennen sitä stageta muutokset normaalisti git add:lla).

- `git status` - Näyttää staged tilassa olevat tiedostot.

- `git diff` - Näyttää erot tiedostojen työtila versioissa verrattuna local repossa oleviin versioihin. Eli näyttää muutokset, joita ei ole commitettu.

- `git reset` - Tyhjentää tiedostot staged tilasta, eli jos olet tehnyt git add jonkun tiedoston niin git reset poistaa sen tiedoston staged tilasta.

- `git rm <file name>` - Poistaa tiedoston ja asettaa tiedoston poiston staged-tilaan, jonka jälkeen tiedoston poisto voidaan commitoida (jos halutaan poistaa kansio, käytetään laajenninta -r, eli `git rm -r <folder name>`).

- `git checkout` - Poistaa muutokset työtilan versiosta ja palautuu local repossa olevan tuoreimman version mukaiseksi.

- `git checkout <branch name>` - Vaihtaa työtilan nimettyyn haaraan.

- `git revert <commit>` - Jos olet jo commitoinut muutokset ja haluatkin palata takaisin aikaisempaan tilaan.

- `git branch testing` - Luo uuden testing-nimisen haaran.

- `git checkout -b <branch name>` - Luo uuden haaran ja vaihtaa työtilan tähän uuteen haaraan.

- `git fetch <nameOfTheRemoteRepo>` - Lataa remote repositoryn tiedot paikalliseen repositoryyn, mutta ei muuta paikallista repoa.

- `git pull <remotenNimi>` - Hakee nykyisen haaran tiedot etä-reposta ja tekee mergen automaattisesti.

- `git merge <branch name>` - Yhdistää nimetyn haaran muutokset työtilaan.

- `git push` - Tallentaa omat lokaalit muutokset etärepositoryyn.

- `git --help` - Listaa hyödyllisimmät git komennot.

- `git clone <repository-url>` - Kloonaa etärepositoryn paikalliseen repositoryyn.

### 5. Muita git komentoja

- `git merge no -ff` - Pakoittaa mergeen kommitin välittämättä siitä onko siihen tullut mitään muutoksia. Tämän avulla haaran olemassaolo tallentuu historiaan vaikka se myöhemmin poistettaisiinkin.

- `git stash` - Piiloittaa haaran missä olet. Voit palauttaa haaran komennolla `git stash apply` (Huom! Kannattaa tehdä vain yksi stash, useimpien stash:en käytöstä voi aiheutua päänvaivaa) Komennolla `git stash drop` voit poistaa kyseisen stash:n.

- `git clean` - Poistaa kaikki untracked-tiedostot, joita ei ole mainittu .gitignore tiedostossa.

- `git tag -a "kommitin_nimi" -m "viestisi"` - Voit kirjata muistiin ns. "leiman" tiettyyn kommittiin. Tämä on hyödyllistä esimerkiksi versioinnin merkinnöissä.

### 6. Ensimmäisen repositoryn luonti omalle koneelle

Avaa Bash-komentokehote kansiossa, josta haluat tehdä repositoryn tai siirry oikeaan kansioon komennolla
`cd <kansio>`

Voit myös luoda Bashin kautta kansion johon haluat reposirotyn tehdä komennoilla `mkdir <kansion nimi>` jonka jälkeen siirtyä kansioon komennolla `cd <kansio>`

Anna sitten seuraavat komennot:
1. `git init`
2. `git add .`
3. `git commit -m 'Ensimmäinen commit'`

### 7. Miten viedä muutokset omasta repositorystä etärepositoryyn
1. `git remote add origin https://github.com/user/example.git`
2. `git push origin master`

### 8. Haarat ja miksi niitä tarvitaan
Haarat `branch` ovat mainio keino pitää saman projektikokonaisuuden eri kehityisvaiheita erillään toisistaan kuitenkin pitäen ne samassa repositoryssä. Yleisimpiä haarakehyksiä ja haarojen käyttöä erilaisissa projekteissa löytyy [tästä linkistä](https://nvie.com/posts/a-successful-git-branching-model/).

Haarojen tarkoitusperä on siis pitää esimerkiksi kehityksessä olevan sovelluksen valmiit testatut osat master haarassa ja toteuttaa testausta sekä jatkokehitystä esimerkiksi development haarassa. Lisäksi voidaan hyvin käyttää omia haaroja ei niin tärkeille komponenteille tai ideoille.
Tällä tavoin ohjelmistokehittäjä voi turvata ettei mikään erillinen osuus projektissa vaikuta mihinkään muuhun, ennenkuin hän näin päättää ja yhdistää `merge` haaran masteriin.

Ennen kuin siirryt haaroista toiseen, muista aina commitoida muutoksesi! Staging-alue ei ole riippuvainen mistään haarasta, joten jos jätät staging-alueella olevat muutokset committoimatta ja vaihdat haaraa, nämä samat muutokset säilyvät staging-alueella. Muutokset siirtyvät haaraan vasta commit-komennon jälkeen.

Yleisesti ottaen masterissa ei koodata mitään ja se toimiikin vain loppusijaintina täydelliselle koodille mitä ei tulla enää muuttamaan.

[Luvusta 4](#4-yleisimpiä-git-komentoja) löydät erilaisia git-komentoja, joilla luoda haaroja, navigoida eri haarojen välillä sekä yhdistää haaroja.


### 9. Merge conflict! Mitä tapahtui, mitä teen?
Merge conflicteja tapahtuu silloin kun yhdistettävissä haaroissa on keskenään ristiriitaisia muutoksia ja Git ei tiedä, mitkä niistä tulisi sisällyttää committiin.

 Tällöin on käsin ratkaistava konfliktit ja valittava pidettävät koodit. Git ilmoittaa, missä kansiossa konflikti on tapahtunut ja toisensa poissulkevat commitit on eroteltu tiedostossa:
 - `<<<<<<` kertoo,mistä konflikti alkaa
 - `======` erottaa muutokset haarojen välillä
 - `>>>>>>` ilmoittaa, milloin konflikti loppuu

 Tarkista kumpi otetaan käyttöön, jonka jälkeen poista konflikti merkit, tallenna tiedostot ja commitoi koodi. Lisää tietoa merge konfliktien korjaamiseen löytyy [täältä] https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts)

### 10. Muita huomioita
- `.gitignore` - on tiedosto, jossa voidaan määritellä etärepositoriosta pois jätettävät tiedostot. Gitignore tiedostoa hyödyntämällä voimme jättää tarpeettomat ja mahdollisesti arkaluontoiset tiedot (salasanat tai muut kehityksessä tarvittavat tiedot) pois etärepositoriosta.

- `git config` - voidaan antaa gitille uusia asetuksia
- `git config --global --list` listaa käytössä olevat globaalit asetukset

Esim.
- `git config --global core.autocrlf false` Kertoo gitille, että ei muuta rivinvaihtoja kun tehdään commit. Hyödyllistä, jos projektia on kehittämässä henkilöitä, joilla on eri käyttöjärjestelmiä. Käyttöjärjestelmät rivittävät tiedostoja eri tavoin.


### 11. Mikä ihmeen Github?

GitHub on verkkosivusto, joka tarjoaa paikan Git-versionhallintaa käyttäville ohjelmakehitysprojekteille. Git itsessään on komentoriviohjelma, jolle Github tarjoaa erään graafisen käyttöliittymän. Gitin lisäksi GitHub tarjoaa projekteille toimintoja kuten bugienseurannan, kehitystoiveet, tehtävien hallinta ja wiki.

Git-versionhallintaa toteutetaan siis paikallisesti, mutta viemällä projektin Githubiin tai vastaavaan palveluun saadaan toteutettua Gitillä etärepository, jonka voi halutessa jakaa muiden käytttöön.

Huhtikuun 2016 GitHubin raportin mukaan sillä oli yli 14 miljoonaa käyttäjää ja yli 35 miljoonaa ohjelmavarastoa. Tämä tekee siitä maailman suurimman lähdekoodi-verkkopalvelun.

[Tutustu Githubiin](https://github.com/)