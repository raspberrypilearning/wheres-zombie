## Testează GPS-ul

Probabil dorești să testezi dacă pictograma jucătorului tău se mișcă în timp ce te deplasezi. Pentru a face acest lucru, va trebui să ieși afară. Acest lucru poate fi destul de incomod în timp ce țineți un computer, așa că hai să încărcăm pagina web pe internet, astfel încât să o poți accesa pe telefon!

### Indicații de siguranță importante

Nu uita că atunci când încărci lucrurile pe internet, oricine le poate vedea. Dacă ai centrat harta pe latitudinea și longitudinea casei tale, oricine accesează pagina web poate vedea exact unde locuiești. Este mai sigur să îți configurezi harta zombie într-o zonă comună, cum ar fi un parc sau centrului orașului, astfel încât să nu îți dai datele tale personale.

Pentru ca GPS-ul să funcționeze, va trebui să activezi serviciile de locație de pe telefon. Fii conștient că acest lucru înseamnă că telefonul tau îți va urmări poziția exactă. Nu este niciodată o idee bună să postezi locația ta exactă în public pe internet, așa că pentru a fi în siguranță, dezactivează din nou serviciile de locație după ce ai jucat jocul cu zombi, pentru a vă asigura că nici o altă aplicație nu iți poate folosi datele locației. Locația ta va fi utilizată doar de jocul zombi în pagina web creată — știi exact ce face acest cod, pentru că tu l-ai scris!

### Încarcă-ți codul

Poți încărca jocul cu zombie pe orice serviciu care oferă găzduire web. Dacă ai deja vreun serviciu disponibil pentru tine, în acest caz, nu ezita să îl folosești. Am ales să folosim [GitHub Pages](https://pages.github.com/){:target="_blank"} deoarece este un serviciu de încredere și ușor de utilizat. Pentru a începe, urmează acești pași:

+ Înscrie-te pentru un [cont GitHub](https://github.com/join){:target="_blank"}

+ Accesează [pagina cu instrucțiuni](https://pages.github.com/){:target="_blank"} și dă click pe **Project site** și **Start from scratch**

![Github pages](images/github-pages.png)

+ Urmează instrucțiunile pentru a crea un fișier index așa cum este descris, dar în loc să tastezi `<h1>Hello</h1>`, lipește codul din fișierul `index.html` înainte de comiterea acestuia

+ De asemenea, va trebui să dai click pe butonul **Upload files** și să încarci fișierele emoji pe care le utilizezi

+ În final, urmărește pasul 4 din pagina cu instrucțiuni pentru a configura ramura principală ca site GitHub Pages, apoi vizualizează-ți pagina tastând adresa într-un browser.

## Restricționează-ți cheia API

După ce ai pus codul online, cheia ta API Google Maps este vizibilă pentru toată lumea. Cineva ar putea să o ia și să o folosească fără permisiunea ta. Poți împedica acest lucru să se întâmple, restricționând unde poate fi utilizat, astfel încât să poată fi utilizat doar pe site-ul tău web.

+ Întoarce-te la [Google APIs console](https://console.developers.google.com/flows/enableapi?apiid=picker&credential=client_key){:target="_ blank"} și dă click pe **Select a project** în stânga sus a paginii.

![Selectează un proiect](images/select-a-project.png)

+ Selectează proiectul pe care l-ai făcut când ai configurat cheia API. Acest lucru ar putea fi încă numit **My project** dacă nu i-ai schimbat numele.

+ Dă click pe **Credentials** din stânga, apoi dă click pe cheia API.

![Selectează un proiect](images/credentials.png)

+ Sub **Key restriction**, selectează **HTTP referrers** și în casetă, adaugă adresa URL de bază a site-ului tău web, cu un `*` la fiecare capăt. De exemplu, codul meu a fost găzduit la `http://lawsie.github.io/`, așa că am pus `*lawsie.github.io/*`. Dă click pe **Save**.

![Restricție cheie](images/key-restriction.png)

+ Cheia ta ar trebui să funcționeze acum doar pe site-ul tău web, și nu în altă parte. Reține că, dacă încerci acum să privești harta de pe computer, aceasta nu va funcționa deoarece solicitarea nu vine de pe site-ul tău web. S-ar putea să dorești să creezi o cheie API suplimentară care nu este restricționată și să utilizezi NUMAI acea cheie de pe computerul tău privat pentru testare.