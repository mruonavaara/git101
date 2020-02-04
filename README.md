# git101
Git-opas Haaga-Helian opiskelijoille

Sisällys
### Yleisimpiä git-komentoja

- git init - luo paikallisen tyhjän repositoryn
- git add . - vertaa hakemistoa local repoon ja siirtää kaikki muutokset tilaan staged, eli nyt ne ovat valmiita commitoitavaksi
local repoon. Koskee myös tiedoston luomisia ja poistamisia. 

- git commit - tallettaa staged tilassa olevat tiedostot local repositoryyn.
-git commit --amend - tällä voit lisätä edelliseen committiin muutoksia, jotka unohdit tehdä(ennen sitä stageta muutokset normaalisti git add:lla)
- git status - näyttää staged tilassa olevat tiedostot
- git diff - näyttää erot tiedostojen työtila versioissa verrattuna local repossa oleviin versioihin. Eli näyttää muutokset, joita ei ole commitettu
- git reset - tyhjentää filut staged tilasta, eli jos olet tehnyt git add jonkun tiedoston niin git reset poistaa sen tiedoston staged tilasta

git checkout - poistaa muutokset työtilan versiosta ja palautuu local repossa olevan tuoreimman version
- Ensimmäisen repositoryn luonti omalle koneelle
- **Mikä Git on ja mihin sitä tarvitaan?**
Git on versionhallinta. Versionhallinnalla tarkoitetaan palvelua, joka säilyttää koodia toisin sanoen varmuuskopio koodista. Versionhallinnan avulla voidaan muutosten tekemisen jälkeenkin palata aiempiin versioihin, jos esim. jotain menee pieleen. Koodin lisäksi versionhalinnan avulla tehdyt muutokset on helppo dokumentoida.Git on Ilmainen. Git on Hajautettu, siinä ei siis ole minkäänlaista keskitettyä palvelinta. Jokainen Git-tietovarasto on itsenäinen.

### Miten viedä muutokset omasta repositorystä etärepositoryyn
### Haarat ja miksi niitä tarvitaan
### Merge conflict! Mitä tapahtui, mitä teen?
Merge conflicteja tapahtuu silloin kun yhdistettävissä haaroissa on keskenään ristiriitaisia muutoksia ja git ei tiedä, mitkä niistä tulisi sisällyttää committiin.
### Komentorivin käyttö
### Git:n asennus
