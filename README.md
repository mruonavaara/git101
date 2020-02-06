# git101
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
Git on versionhallinta. Versionhallinnalla tarkoitetaan palvelua, joka säilyttää koodia toisin sanoen varmuuskopio koodista. Versionhallinnan avulla voidaan muutosten tekemisen jälkeenkin palata aiempiin versioihin, jos esim. jotain menee pieleen. Koodin lisäksi versionhalinnan avulla tehdyt muutokset on helppo dokumentoida. Git on Ilmainen. Git on Hajautettu, siinä ei siis ole minkäänlaista keskitettyä palvelinta. Jokainen Git-tietovarasto on itsenäinen.

### 2. Git:n asennus
Git:n käyttämiseksi on git-ohjelmisto oltava asennettuna tietokoneella, jolla sitä halutaan käyttää. Git-ohjelmiston asentamiseksi löytyy varmasti useita eri ohjeita ympäri internettiä, alla git:n omat ohjeet

[Git asennusohjeet](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)



### 3. Komentorivin käyttö

### 4. Yleisimpiä git-komentoja

- `git init` - luo paikallisen tyhjän repositoryn

- `git add .` - vertaa hakemistoa local repoon ja siirtää kaikki muutokset tilaan staged, eli nyt ne ovat valmiita commitoitavaksi local repoon. Koskee myös tiedoston luomisia ja poistamisia.

- `git commit` - tallettaa staged tilassa olevat tiedostot local repositoryyn.

- `git commit --amend` - tällä voit lisätä edelliseen committiin muutoksia, jotka unohdit tehdä(ennen sitä stageta muutokset normaalisti git add:lla)

- `git status` - näyttää staged tilassa olevat tiedostot

- `git diff` - näyttää erot tiedostojen työtila versioissa verrattuna local repossa oleviin versioihin. Eli näyttää muutokset, joita ei ole commitettu

- `git reset` - tyhjentää filut staged tilasta, eli jos olet tehnyt git add jonkun tiedoston niin git reset poistaa sen tiedoston staged tilasta

- `git checkout` - poistaa muutokset työtilan versiosta ja palautuu local repossa olevan tuoreimman version

### 5.Ensimmäisen repositoryn luonti omalle koneelle
Avaa bash-komentokehote kansiossa, josta haluat tehdä repositoryn. 
Anna sitten seuraavat komennot:
1. `git init`
2. `git add .`
3. `git commit -m 'Ensimmäinen commit'`

### 6. Miten viedä muutokset omasta repositorystä etärepositoryyn
1. `git remote add origin https://github.com/user/example.git`
2. `git push origin master`

### 7. Haarat ja miksi niitä tarvitaan

### 8. Merge conflict! Mitä tapahtui, mitä teen?
Merge conflicteja tapahtuu silloin kun yhdistettävissä haaroissa on keskenään ristiriitaisia muutoksia ja git ei tiedä, mitkä niistä tulisi sisällyttää committiin.