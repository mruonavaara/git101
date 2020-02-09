# git101 ![git-logo](images/Git-logo.png)
Git-opas Haaga-Helian opiskelijoille

Sisällys
1. Mikä on Git ja mihin sitä tarvitaan?
2. Git:n asennus
3. Komentorivin käyttö
4. Yleisimpiä git-komentoja
5. Ensimmäisen repositoryn luonti omalle koneelle
6. Miten viedä muutokset omasta repositorystä etärepositoryyn
7. Haarat ja miksi niitä tarvitaan
8. Merge conflict! Mitä tapahtui, mitä teen?

### 1. Mikä Git on ja mihin sitä tarvitaan?
Git on versionhallinta. Versionhallinnalla tarkoitetaan palvelua, joka säilyttää koodia. Toisin sanoen varmuuskopio koodista. Versionhallinnan avulla voidaan muutosten tekemisen jälkeenkin palata aiempiin versioihin, jos esim. jotain menee pieleen. Koodin lisäksi versionhalinnan avulla tehdyt muutokset on helppo dokumentoida. Git on Ilmainen. Git on hajautettu, siinä ei siis ole minkäänlaista keskitettyä palvelinta. Jokainen Git-tietovarasto on itsenäinen.

### 2. Git:n asennus
Git:n käyttämiseksi on git-ohjelmisto oltava asennettuna tietokoneella, jolla sitä halutaan käyttää. Git-ohjelmiston asentamiseksi löytyy varmasti useita eri ohjeita ympäri internettiä, alla git:n omat ohjeet

[Git asennusohjeet](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

#### 2.1 Konfigurointi
##### 2.1.1 Käyttäjätiedot
Jokaiseen versionhallintaan talletettavaan muutokseen tallennetaan muutoksen tehneen käyttäjän nimi ja sähköpostiosoite. Git-ohjelmiston asentamisen jälkeen olisikin hyvä asettaa käyttäjätiedot komennoilla:

- `git config --global user.name "<username>"`
- `git config --global user.email <email>`

`<username>` ja `<email>` kohdat korvataan omalla nimellä ja sähköpostilla. Käyttäjätiedot tarvitsee asettaa vain kerran tietokoneelle. --global -tarkennin tarkentimella tiedot asetetaan siten, että asetukset ovat tietokoneen käyttäjäkohtaiset.

##### 2.1.2 Tekstieditori
Git-ohjelmistoa käyttäessä tulee esiin tilanteita, joissa on tarve käyttää tekstieditoria. Ohjelmiston asentamisen jälkeen oletusarvoinen tekstieditori on [vi](https://fi.wikipedia.org/wiki/Vi). Vi:n käyttäminen voi tuntu haastavalta (ohjeita tosin löytyy esim [täältä](https://fi.wikipedia.org/wiki/Vi#Peruskomennot)), joten git-ohjelmistossa on mahdollista vaihtaa tekstieditoria komennolla:
- `git config --global core.editor "<editor-and-options>"`

Tekstieditoriksi voi yrittää asettaa varmaan minkä tahansa ohjelman. Perusteelliset ohjeet eri editorien asettamiseksi löytyy [täältä](https://git-scm.com/book/tr/v2/Appendix-C%3A-Git-Commands-Setup-and-Config#_core_editor).

### 3. Komentotulkin käyttö
Komentoliittymässä ajetaan tyypillisesti komentotulkkia. Tällöin käyttäjä kirjoittaa komentoriville käynnistettävän ohjelman nimen tai komentotulkin sisäisen komennon mahdollisine parametreineen ja painaa syöttöpainiketta, jolloin komentotulkki käsittelee käskyn ja tulostaa vastineen näytölle.

Komentoliittymän käyttö ei välttämättä vaadi suurta järjestelmän tuntemusta, sillä komennot ovat usein lyhennyksiä selväkielisistä englanninkielisistä sanoista, ja niille on yleensä saatavilla käytönaikainen ohje komennoilla help tai man.

Yleensä kaikki git-komennot annetaankin komentotulkkia käyttäen. Komennolla `git help` saadaan lista komennoista, jotka voidaan suorittaa.

### 4. Yleisimpiä git-komentoja

- `git init` - luo paikallisen tyhjän repositoryn

- `git add .` - vertaa hakemistoa local repoon ja siirtää kaikki muutokset tilaan staged, eli nyt ne ovat valmiita commitoitavaksi local repoon. Koskee myös tiedoston luomisia ja poistamisia.

- `git commit` - tallettaa staged tilassa olevat tiedostot local repositoryyn.

- `git commit --amend` - tällä voit lisätä edelliseen committiin muutoksia, jotka unohdit tehdä(ennen sitä stageta muutokset normaalisti git add:lla)

- `git status` - näyttää staged tilassa olevat tiedostot

- `git diff` - näyttää erot tiedostojen työtila versioissa verrattuna local repossa oleviin versioihin. Eli näyttää muutokset, joita ei ole commitettu

- `git reset` - tyhjentää tiedostot staged tilasta, eli jos olet tehnyt git add jonkun tiedoston niin git reset poistaa sen tiedoston staged tilasta

- `git checkout` - poistaa muutokset työtilan versiosta ja palautuu local repossa olevan tuoreimman version
- `git checkout <branch name>` - vaihtaa työtilan nimettyyn haaraan

- `git branch testing` - luo uuden testing-nimisen haaran

- `git merge <branch name>` - yhdistää nimetyn haaran muutokset työtilaan

- `git push` - tallentaa omat lokaalit muutokset etärepositoryyn.

- `git --help` - Listaa hyödyllisimmät git komennot.

### 5.Ensimmäisen repositoryn luonti omalle koneelle
Avaa bash-komentokehote kansiossa, josta haluat tehdä repositoryn tai siirry oikeaan kansioon komennolla 
`cd <kansio>`
Anna sitten seuraavat komennot:
1. `git init`
2. `git add .`
3. `git commit -m 'Ensimmäinen commit'`

### 6. Miten viedä muutokset omasta repositorystä etärepositoryyn
1. `git remote add origin https://github.com/user/example.git`
2. `git push origin master`

### 7. Haarat ja miksi niitä tarvitaan
Haarat `branch` ovat mainio keino pitää saman projektikokonaisuuden eri kehityisvaiheita erillään toisistaan kuitenkin pitäen ne samassa repositoryssä. Yleisimpiä haarakehyksiä ja haarojen käyttöä erilaisissa projekteissa löytyy [tästä linkistä](https://nvie.com/posts/a-successful-git-branching-model/).

Haarojen tarkoitusperä on siis pitää esimerkiksi kehityksessä olevan sovelluksen valmiit testatut osat master haarassa ja toteuttaa testausta sekä jatkokehitystä esimerkiksi development haarassa. Lisäksi voidaan hyvin käyttää omia haaroja ei niin tärkeille komponenteille tai ideoille.
Tällä tavoin ohjelmistokehittäjä voi turvata ettei mikään erillinen osuus projektissa vaikuta mihinkään muuhun, ennenkuin hän näin päättää ja yhdistää `merge` haaran masteriin.

Yleisesti ottaen masterissa ei koodata mitään ja se toimiikin vain loppusijaintina täydelliselle koodille mitä ei tulla enää muuttamaan.


### 8. Merge conflict! Mitä tapahtui, mitä teen?
Merge conflicteja tapahtuu silloin kun yhdistettävissä haaroissa on keskenään ristiriitaisia muutoksia ja git ei tiedä, mitkä niistä tulisi sisällyttää committiin.

 Tällöin on käsin ratkaistava konfliktit ja valittava pidettävät koodit. Git ilmoittaa, missä kansiossa konflikti on tapahtunut ja toisensa poissulkevat commitit on eroteltu tiedostossa:
 - <<<<<< = kertoo,mistä konflikti alkaa
 - ====== = erottaa muutokset haarojen välillä
 - >>>>>> = ilmoittaa, milloin konflikti loppuu
 Tarkista kumpi otetaan käyttöön, jonka jälkeen poista konflikti merkit ja commitoi koodi.
