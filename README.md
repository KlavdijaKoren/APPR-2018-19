# Analiza podatkov s programom R, 2018/19

**Klavdija Koren**

Repozitorij z gradivi pri predmetu APPR v študijskem letu 2018/19

* [![Shiny](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/jaanos/APPR-2018-19/master?urlpath=shiny/APPR-2018-19/projekt.Rmd) Shiny
* [![RStudio](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/KorenK17/APPR-2018-19/master?urlpath=rstudio) RStudio


## Analiza kulturnih domov, glasbe in gledališč

Moja projektna naloga govori o kulturnih prireditvah v različnih kulturnih ustanovah oz. domovih. Podatke bom predstavila v tabelah naštetih spodaj. Zanimali me bodo predvsem podatki o določenih prireditvah na primer vrste kulturnih prireditev in njihovo število gledano letno ter število obiskovalcev. Govorila bom tudi o prodaji vstopnic na primer prihodek od prodaj, brezplačne vstopnice, povprečne cene le teh ter ob tem omenila tudi vir pihodkov in stroške različnih kulturnih ustanov oz. prireditev. Na kratko bom govorila tudi o festivalih, ki pa so le podkategorija mojih prejšnjih podatkov. Kot zanimivost pa bom dodala tudi podatke o ustanovah, ki omogočajo dostop gibalnim in senzorno oviranim osebam.

Vse podatke bom pridobila na statističnemu uradu Republike Slovenije (SI-STAT) pod tematiko Kultura. 

## Tabele

* Tabela 1: vrsta predstavitev, vrsta enote (ustanove), leto, Slovenija
* Tabela 2: vrsta predstavitev, število predstavitev, število obiskovalcev, leto, SLovenija
* Tabela 3: vrsta enote, število prireditev, prihodek od prodaje vstopic, brezplačne vstopnice, viri prihodkov in stroški, leto, Slovenija
* Tabela 4: vrsta festivalov, vrsta enote, število festivalov, število festivalnih prireditev, leto, Slovenija
* Tabela 5: dostop gibalno in senzorno oviranih oseb, vrsta dostopa, vrsta enote, leto, Slovenija

## Viri

* https://pxweb.stat.si/pxweb/Database/Dem_soc/10_kultura/03_10807_kultura_oder/03_10807_kultura_oder.asp

Viri tabel:
* Tabela 1: https://pxweb.stat.si/pxweb/Dialog/varval.asp?ma=1080706S&ti=&path=../Database/Dem_soc/10_kultura/03_10807_kultura_oder/&lang=2

* Tabela 2: https://pxweb.stat.si/pxweb/Dialog/varval.asp?ma=1080710S&ti=&path=../Database/Dem_soc/10_kultura/03_10807_kultura_oder/&lang=2

* Tabela 3: https://pxweb.stat.si/pxweb/Dialog/varval.asp?ma=1080715S&ti=&path=../Database/Dem_soc/10_kultura/03_10807_kultura_oder/&lang=2, https://pxweb.stat.si/pxweb/Dialog/varval.asp?ma=1080775S&ti=&path=../Database/Dem_soc/10_kultura/03_10807_kultura_oder/&lang=2

* Tabela 4: https://pxweb.stat.si/pxweb/Dialog/varval.asp?ma=1080740S&ti=&path=../Database/Dem_soc/10_kultura/03_10807_kultura_oder/&lang=2

* Tabela 5: https://pxweb.stat.si/pxweb/Dialog/varval.asp?ma=1080760S&ti=&path=../Database/Dem_soc/10_kultura/03_10807_kultura_oder/&lang=2

## Program

Glavni program in poročilo se nahajata v datoteki `projekt.Rmd`.
Ko ga prevedemo, se izvedejo programi, ki ustrezajo drugi, tretji in četrti fazi projekta:

* obdelava, uvoz in čiščenje podatkov: `uvoz/uvoz.r`
* analiza in vizualizacija podatkov: `vizualizacija/vizualizacija.r`
* napredna analiza podatkov: `analiza/analiza.r`

Vnaprej pripravljene funkcije se nahajajo v datotekah v mapi `lib/`.
Podatkovni viri so v mapi `podatki/`.
Zemljevidi v obliki SHP, ki jih program pobere,
se shranijo v mapo `../zemljevidi/` (torej izven mape projekta).

## Potrebni paketi za R

Za zagon tega vzorca je potrebno namestiti sledeče pakete za R:

* `knitr` - za izdelovanje poročila
* `rmarkdown` - za prevajanje poročila v obliki RMarkdown
* `shiny` - za prikaz spletnega vmesnika
* `DT` - za prikaz interaktivne tabele
* `rgdal` - za uvoz zemljevidov
* `digest` - za zgoščevalne funkcije (uporabljajo se za shranjevanje zemljevidov)
* `readr` - za branje podatkov
* `rvest` - za pobiranje spletnih strani
* `reshape2` - za preoblikovanje podatkov v obliko *tidy data*
* `dplyr` - za delo s podatki
* `gsubfn` - za delo z nizi (čiščenje podatkov)
* `ggplot2` - za izrisovanje grafov
* `mosaic` - za pretvorbo zemljevidov v obliko za risanje z `ggplot2`
* `maptools` - za delo z zemljevidi
* `extrafont` - za pravilen prikaz šumnikov (neobvezno)

## Binder

Zgornje [povezave](#analiza-podatkov-s-programom-r-201819)
omogočajo poganjanje projekta na spletu z orodjem [Binder](https://mybinder.org/).
V ta namen je bila pripravljena slika za [Docker](https://www.docker.com/),
ki vsebuje večino paketov, ki jih boste potrebovali za svoj projekt.

Če se izkaže, da katerega od paketov, ki ji potrebujete, ni v sliki,
lahko za sprotno namestitev poskrbite tako,
da jih v datoteki [`install.R`](install.R) namestite z ukazom `install.packages`.
Te datoteke (ali ukaza `install.packages`) **ne vključujte** v svoj program -
gre samo za navodilo za Binder, katere pakete naj namesti pred poganjanjem vašega projekta.

Tako nameščanje paketov se bo izvedlo pred vsakim poganjanjem v Binderju.
Če se izkaže, da je to preveč zamudno,
lahko pripravite [lastno sliko](https://github.com/jaanos/APPR-docker) z želenimi paketi.

Če želite v Binderju delati z git,
v datoteki `gitconfig` nastavite svoje ime in priimek ter e-poštni naslov
(odkomentirajte vzorec in zamenjajte s svojimi podatki) -
ob naslednjem.zagonu bo mogoče delati commite.
Te podatke lahko nastavite tudi z `git config --global` v konzoli
(vendar bodo veljale le v trenutni seji).

