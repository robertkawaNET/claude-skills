# Przewodnik stylu tutoriala (po polsku)

Ten plik jest jedynym miejscem, w którym zapisano formaty i konwencje. Szkielet pliku (części, kolejność, szablony) jest w `tutorial-template.md` - tam znajdziesz układ, tutaj zasady. Słowa w `{...}` to miejsca do uzupełnienia.

## 1. Język

- Proza po polsku. Terminy angielskie, etykiety interfejsu i kod zostają po angielsku (nie tłumaczymy nazw przycisków, kluczy YAML, poleceń).
- Każdy termin angielski wyjaśnij prostym polskim **przy pierwszym użyciu** w pliku (np. "CI = ciągła integracja, czyli automatyczny build i testy po każdej zmianie"). Potem używaj już samego terminu.
- Żargon techniczny (YAML, JSON, REST API, fork, Docker, label, merge commit, runner i podobne) też objaśnij przy pierwszym użyciu, krótko w nawiasie, np. "YAML (format pliku konfiguracyjnego z wcięciami)". Dotyczy to także słów polskich, które w IT znaczą co innego niż w życiu.
- Krótkie zdania. Zero niewyjaśnionego żargonu. Pisz do osoby, która widzi temat pierwszy raz.
- Nazwy własne produktów i funkcji zapisuj tak, jak w interfejsie lub dokumentacji.
- Ton: rzeczowy, w drugiej osobie ("otwórz", "zobacz"). Bez emoji.
- Kod, komendy i identyfikatory w znakach `` ` ``; bloki kodu z oznaczeniem języka.

## 2. Środki dydaktyczne

- **Tabele** do porównań i list opcji (kolumny: co, kiedy, uwagi).
- **Drzewka ASCII** do hierarchii i zależności (blok kodu bez języka).
- **Kod z numerowanymi komentarzami** `(1)..(n)` w tej samej linii, a pod blokiem lista "Objaśnienie:" z tymi samymi numerami.
- **Wywołania "egzamin je lubi"**: w pliku luk blockquote `> **Egzamin je lubi:**` z krótką listą rzeczy, o które pytają na egzaminie (limity, wartości domyślne, pułapki w nazwach). W sekcjach tutoriala modułu wystarcza krótka fraza w tekście, np. "(egzamin je lubi)" w nagłówku lub zdaniu.
- **Eksperymenty "zepsuj to"**: w ćwiczeniach jedno zadanie celowo psuje konfigurację (usuń klucz, zmień wartość), a **Sprawdź** opisuje oczekiwany błąd. Uczy czytać komunikaty.
- **Przypis** jako `<sub>* ...</sub>` pod sekcją, gdy wyjątek zaśmieciłby główny wywód.

## 3. Znaczniki źródeł

Pierwsza linia pod każdym nagłówkiem `##` w częściach teorii i w pliku luk ma postać (w ćwiczeniach tylko gdy treść pochodzi spoza modułu; quiz i pytania kontrolne jej nie mają):

`_Źródło: <znacznik> [+ <znacznik>]_`

Znaczniki:

- `[unit <id>]` - jednostka (unit) modułu Microsoft Learn; `<id>` to prefiks pliku w `sources/<moduł>/` (np. `2`, `2b`).
- `[moduł kursu: <slug>]` - inny moduł tego samego kursu.
- `[spoza kursu, ale na egzaminie (domena N): <slug or URL>]` - temat z listy umiejętności egzaminu, którego żaden moduł kursu nie uczy.
- `[docs: <URL>]` - oficjalna dokumentacja produktu.
- `[autor]` - dodane przez autora tutoriala. Warianty: `[autor: test <data>]` (sprawdzone testem w podanym dniu) i `[autor: niezweryfikowane]` (jeszcze nie sprawdzone).

Zasady umiejscowienia:

- Znacznik w linii pod nagłówkiem opisuje całą sekcję. Gdy sekcja miesza źródła, dodaj **znacznik w treści** na końcu jednego punktu listy lub akapitu (np. `... [unit 2]`).
- Każdy cytowany `[unit ...]` i `[docs: ...]` musi mieć zapisany plik w `sources/` (patrz sekcja 11).
- Informacje zmienne (wersje, limity) mają znacznik źródła przy samym zdaniu oraz datę (patrz "Pieczątka wersji").
- Nie wymyślaj nowych znaczników.
- **Legenda tylko tutaj.** Nagłówek tutoriala ma jedną linię: nazwy znaczników i odsyłacz do pełnej legendy (np. `Źródła: [unit] = Learn, [docs] = dokumentacja, [autor] = dodane przez autora; pełna legenda: plik startowy lub przewodnik stylu §3`). Nie kopiuj całej legendy do tutoriala.
- **Sekcja z jednego źródła.** Gdy cały materiał sekcji pochodzi z jednej jednostki, wystarcza linia `_Źródło:_`; nie powtarzaj znaczników w treści.
- **Twierdzenia autora.** Każde twierdzenie techniczne napisane z własnej wiedzy (limity, kolory, komunikaty błędów, numery wersji, nazwy opcji) sprawdź w dokumentacji produktu (fetch) i oznacz `[docs: URL]`. Gdy nie da się sprawdzić: `[autor: niezweryfikowane]`. Żadnych konkretów bez znacznika. Numery wersji i tagi użyte w przykładach (np. `@vN.M`) muszą istnieć: sprawdź stronę wydań lub tagów repozytorium (w pierwszym przebiegu w tutorialu znalazł się nieistniejący tag).

## 4. Formaty

### 4.1 Flaga błędu w materiale Microsoftu

Blockquote, dokładnie w tej postaci:

```
> **UWAGA - błąd w materiale Microsoftu** (unit <id>): <co podaje moduł> -> <co jest poprawne>. Źródło: <URL>.
```

Flagę wstaw w sekcji, której dotyczy błąd. Poprawna wartość musi mieć źródło w oficjalnej dokumentacji (nie z pamięci). Nie flaguj różnic stylu ani starych numerów wersji (to idzie do pieczątki wersji).

### 4.2 Quiz modułu

- Część quizu ma po jednej sekcji `##` na pytanie: nagłówek = treść pytania w skrócie.
- Pod nagłówkiem: `-> *<poprawna odpowiedź>*` i krótkie wyjaśnienie, potem **pułapki** (dlaczego pozostałe opcje są błędne).
- Gdy Learn **nie pokazuje** poprawnej odpowiedzi, odpowiedź jest wnioskowana z treści jednostek, a pytanie kończy marker:

`*(odpowiedź wnioskowana - Learn nie pokazuje odpowiedzi; uzasadnienie: unit <id>, sekcja <X>)*`

- Wariant krótszy (gdy pytań jest dużo): jedno zdanie pod nagłówkiem części quizu mówi, że odpowiedzi są wnioskowane, a przy każdym pytaniu zostaje krótki znacznik `*(odpowiedź wnioskowana: unit <id>, sekcja <X>)*`.
- Jeśli źródło pokazuje odpowiedź, marker pomijasz.
- Liczba pytań wynika ze źródła, nigdy z założenia.

### 4.3 Quiz autorski (gdy Learn nie udostępnia pytań)

- Tytuł części: `QUIZ (pytania autorskie - Learn nie udostępnia pytań modułu)`.
- Każde pytanie ma w linii źródła znacznik `[autor]`; format pytania jak w 4.2, ale bez markera wnioskowania (odpowiedź wynika z Twojej własnej sekcji teorii, wskaż ją przez ID sekcji).
- Pytania obejmują te same tematy, które objąłby quiz modułu: pojęcia, pułapki w nazwach, wartości domyślne.
- W raporcie dla użytkownika zaznacz, że quiz jest autorski.

### 4.4 Pytania kontrolne

- Tyle pytań, ile moduł naprawdę uczy (5-12); nigdy nie dopełniaj prawie identycznymi pytaniami. Każde to `##` z numerem części, treść pytania w nagłówku.
- Odpowiedź w `<details>`:

```
<details><summary>Odpowiedź</summary>

{krótka odpowiedź, 1-3 zdania}
</details>
```

- Linia pusta po `<summary>` jest obowiązkowa (inaczej Markdown nie wyrenderuje treści).
- Każda odpowiedź musi zgadzać się z teorią (klucze, liczby, limity sprawdź jawnie).
- Pytania "wymień N rzeczy" i "co się stanie, gdy..." sprawdzają zapamiętanie i rozumienie.

### 4.5 Odnośnik do rozwinięcia (cross-ref)

- W nagłówku ćwiczenia, w linii pod nim: `(rozwinięte w <plik> <§>)`, np. `(rozwinięte w {02-nazwa.md} Ćw. {2.4})`.
- W teorii: `(szczegóły: <plik> <§>)` lub `(patrz <ID sekcji>)`. Odnośnik wskazuje istniejącą sekcję, nigdy plik, którego jeszcze nie ma (wtedy podaj URL modułu).
- W tekście "moduł N" znaczy plik tutoriala `0N-*.md`; zapisz to jednym zdaniem w nagłówku pliku, jeśli używasz takich odwołań.

### 4.6 Pieczątka wersji

Dla numerów wersji, runtime'ów, SKU, wersji API i flag CLI:

```
> Wersje sprawdzone {RRRR-MM-DD} (źródło: {URL}, {URL}): {lista wersji}. {Co mówi moduł Microsoftu i dlaczego na egzaminie liczy się zasada}. Przed użyciem sprawdź {stronę wydań}.
```

Gdy nie da się sprawdzić, zamiast pieczątki wstaw ostrzeżenie: `> Niesprawdzone: {co} - zweryfikuj w {gdzie}.`

## 5. Blok ćwiczenia

Każde ćwiczenie ma ten sam układ (nazwa i kolejność pól są stałe, produkt jest dowolny):

1. `## I<n>. <tytuł>` i opcjonalnie w następnej linii cross-ref `(rozwinięte w <plik> <§>)`.
2. `**Gdzie / Plik:**` - ścieżka pliku (np. `.github/workflows/x.yml`, `main.bicep`) **albo** lokalizacja: ścieżka w portalu (`Portal: Resource groups -> + Create`), powłoka (`Cloud Shell (Bash)`), miejsce w interfejsie.
3. Pełny, uruchamialny kod **albo** numerowane kroki click-path. Żadnych "uzupełnij sam".
4. `**Koszt:**` - **obowiązkowe**, gdy ćwiczenie tworzy zasoby w chmurze lub płatne; w przeciwnym razie pomiń linię. Podaj, co kosztuje, rząd wielkości i jak go uniknąć.
5. `**Zadania:** (a)..` - zadania literowane, w tym co najmniej jeden eksperyment "zepsuj to".
6. `**Sprawdź:**` - po jednym oczekiwanym wyniku na każde zadanie, tą samą literą.
7. `**Sprzątanie:**` - **obowiązkowe**. Dla zasobów w chmurze prawdziwa procedura; gdy nic nie powstało: krótko `brak` (powód tylko, gdy nie jest oczywisty).

Reguły ogólne:

- Linia `Czas:` w nagłówku tutoriala jest szacunkiem opartym na czasach jednostek modułu i liczbie ćwiczeń, z dopiskiem "orientacyjnie"; nie zgaduj.
- Ćwiczenie nie odwołuje się do rzeczy z późniejszych części (żadnych odwołań "w przód").
- Moduł bez jednostki ćwiczeniowej: napisz ćwiczenia dopasowane do produktu (klikanie w portalu, CLI, ćwiczenie na papierze) ze znacznikami `[docs: URL]` + `[autor: niezweryfikowane]` (lub `[autor]`, gdy sprawdzone), z pełnym układem pól powyżej.
- Gdy lab podlinkowany z jednostki ćwiczenia nie zgadza się z tekstem jednostki, zachowaj oba, oznacz część z labu `[unit N]` i dodaj zwykły blockquote `> Uwaga o labie ...`. Formalnej flagi błędu (4.1) używaj tylko, gdy błędna jest sama treść Learn.
- Dopasuj narzędzie do produktu: dla produktów pliku konfiguracyjnego (YAML, Bicep) pełny plik; dla Azure CLI/PowerShell komendy z `--name` i grupą zasobów; dla portalu numerowane kliknięcia z dokładnymi nazwami przycisków.
- Zadania i weryfikacja nie zależą od wcześniejszego stanu sesji (nie zakładaj, że coś "zostało" z poprzedniej rozmowy; zakładaj tylko wcześniejsze ćwiczenia, które wymienisz w **Gdzie / Plik**).

### Koszt i sprzątanie wg rodziny produktu

| Rodzina | **Koszt:** | **Sprzątanie:** |
|---|---|---|
| Chmura (CLI/portal: grupy zasobów, usługi) | Obowiązkowe: SKU, orientacyjna cena lub informacja o darmowym progu (free tier) i jego limit czasowy. | Jedna grupa zasobów na ćwiczenie i `az group delete --name {rg} --yes --no-wait` (lub odpowiednik w portalu: Resource groups -> grupa -> Delete resource group). Potwierdź usunięcie komendą sprawdzającą. |
| Kod i CI/CD (workflowy, repozytoria) | Podaj, czy repo jest publiczne czy prywatne i czy naliczane są minuty runnerów; osobno większe runnery (płatne) i jednostki płatne za magazyn. Bez kosztu: pomiń linię. | Usuń lub wyłącz workflow z harmonogramem, usuń utworzone issues, sekrety i zmienne, przywróć zmienione pliki, usuń repozytorium pomocnicze. |
| Lokalne / bez kosztów (papier, narzędzia lokalne, inne produkty) | Podaj każdy płatny element albo "brak kosztu - <powód>". | Cofnij każdą zmianę i usuń wszystko, co utworzyło ćwiczenie; gdy nic nie powstało: `brak - <powód>`. |

Dodatkowo:

- Dla chmury nazwij grupę zasobów po ćwiczeniu (`rg-{moduł}-i{n}`), żeby jedno polecenie sprzątało wszystko.
- Dla zasobów, które mogą kosztować mimo usunięcia grupy (np. usunięty-ale-odzyskiwalny magazyn kluczy), dopisz krok oczyszczenia.
- Informacje o darmowych progach i cenach mają pieczątkę wersji (4.6).

## 6. Standard pliku luk

Plik luk zbiera tematy z listy umiejętności egzaminu, których **żaden** moduł kursu nie uczy (orphany).

- Jedna sekcja `##` na temat, tytuł: `<NN>.<n> <temat> (domena N)`, gdzie `<NN>` to numer pliku luk, a `<n>` kolejny numer sekcji.
- Pierwsza linia: `_Źródło: [docs: <URL>] [+ ...]_`.
- Treść: pełne, proste wyjaśnienie po polsku: co to jest, po co, jak się tego używa, minimalny przykład (jeśli ma sens) i wywołanie "egzamin je lubi".
- Każda cytowana strona dokumentacji ma wpis w `sources/_gaps/<temat-slug>.md` (format w sekcji 11: cytowany fragment, URL, data pobrania; nie cała strona). Strony pobrane tylko po to, by uzupełnić sekcję modułu, idą tak samo do `sources/_docs/<slug>.md`.
- Numeracja `<NN>.<n>`: NN = numer pliku luk. Domyślna nazwa pliku: `99-luki-egzaminu.md`; gdy w projekcie jest już plik `*luki-egzaminu*.md`, użyj go i kontynuuj jego numerację. Gdy nie ma orphanów, nie twórz pliku (ani pustego, ani szkieletu); w skill-map wpisz "n/a - no orphans".
- Temat, którego nie uczy żaden moduł kursu, a uczy powiązany moduł Learn spoza kursu, jest nadal orphanem: opisz go w pliku luk ze znacznikiem `[spoza kursu, ale na egzaminie (domena N): <moduł>]`.
- Nowe sekcje wstawiasz **przed** `## Samoocena` i kontynuujesz istniejącą numerację.
- Temat należy albo do pliku luk, albo do tutoriala modułu, nigdy do obu. Gdy temat dostaje właściciela-moduł, zgłoś to w raporcie i nie kasuj istniejącej sekcji.
- Plik kończy się sekcją `## Samoocena`.

## 7. Format inwentarza

Plik `sources/<moduł>/_inventory.md`: front matter, a potem jedna tabela.

```
---
module: "{tytuł modułu} ({slug}) - {URL modułu}"
built: {RRRR-MM-DD}
tutorial: {ścieżka pliku tutoriala}
---

| unit | typ | element | token | gdzie w tutorialu |
|---|---|---|---|---|
| {id-jednostki} | {definicja|lista|tabela|kod|uwaga|nagłówek} | {co to za element} | {charakterystyczny token} | {§ID, np. §A1} |
```

- Jeden wiersz na każdy element jednostki: nagłówek H2/H3, listę, tabelę, przykład kodu, definicję, uwagę lub ostrzeżenie.
- Tabela powstaje w kroku 7 z kolumną "gdzie w tutorialu" ustawioną na `DO USTALENIA`; ID sekcji projektujesz w krokach 9-11, a kolumnę uzupełniasz w kroku 12. Na końcu nie może zostać ani `DO USTALENIA`, ani `DO DODANIA`.
- Kolumna "gdzie w tutorialu" ma ID sekcji (`§A1`, kilka po przecinku) albo `pominięte - <powód>`. Pusty wiersz jest błędem.
- Dozwolone powody `pominięte`: nawigacja, obrazy, wymagania wstępne, duplikat, lista marketingowa lub promocyjna, podpowiedzi narzędzi w stylu "Explore with Copilot" (i podobne). Nigdy treść, której można się nauczyć.
- Kolumna `token` (krok 7): jeden charakterystyczny ciąg z elementu (identyfikator z kodu, liczba albo krótka cytowana fraza), który tutorial musi zawierać, jeśli element jest pokryty. Dla elementów bez takiego ciągu (np. nagłówek) wpisz `-`.
- **Kontrola integralności (krok 12).** Dla każdego wiersza oznaczonego jako pokryty wyszukaj `token` w tutorialu (grep) i potwierdź, że występuje w sekcji z kolumny "gdzie w tutorialu". Wiersz, w którym tokena brak, wraca do `DO DODANIA` i jest naprawiany. Powód: w pierwszym przebiegu fałszywie "pokryty" wiersz przeżył, bo ten sam model budował i odhaczał inwentarz.
- Elementy nieuczone w module, a dodane dopiero w tutorialu, nie trafiają do inwentarza (to nie jest treść modułu).

## 8. Format mapy umiejętności i dowód własności

Plik `sources/_exam/skill-map.md` (pisze go tylko skill; to cache przydziału "moduł czy luka" i **jedyne źródło** tabeli pokrycia, patrz sekcja 9):

```
---
exam: {kod egzaminu}
study_guide: {URL}
as_of: {data listy umiejętności, np. RRRR-MM-DD}
built: {RRRR-MM-DD}
---

| umiejętność (study guide) | domena | właściciel (moduł kursu lub "luka") | dowód | data |
|---|---|---|---|---|
| {nazwa umiejętności} | {N} | {slug modułu | luka} | {poziom dowodu + miejsce} | {RRRR-MM-DD} |
```

- Przebuduj plik tylko, gdy zmieni się data listy umiejętności (`as_of`); do tego czasu używaj go bez zmian.
- Punkt study guide bywa złożony: umiejętność uczoną częściowo zapisz jako `moduł X / luka` z dowodem dla każdej części.
- Umiejętność bez właściciela-modułu to orphan i idzie do pliku luk. Temat uczony w dwóch modułach jest w porządku; temat bez dopasowania to orphan.
- **Dowód w dwóch etapach** (bez pobierania wszystkich jednostek wszystkich modułów):
  1. *Kandydaci:* dla każdej umiejętności 1-3 terminy kluczowe i `microsoft_docs_search` (brak filtra URL: wyniki filtruj sam po prefiksie URL modułów kursu); wynik to lista modułów-kandydatów.
  2. *Potwierdzenie:* pobierz (learn-cli fetch) tylko jednostki modułów-kandydatów i sprawdź, że termin naprawdę w nich występuje. Dla modułu bieżącego użyj zapisanych jednostek.
- Poziom dowodu w kolumnie `dowód` (dokładnie jedna z form):
  - `potwierdzone w jednostce X` - termin znaleziony w pobranym tekście jednostki;
  - `kandydat z wyszukiwarki (niepotwierdzone)` - tylko wynik wyszukiwania; dopuszczalny w dużych kursach po zgodzie użytkownika (w przebiegu bez pytań domyślnie dozwolony), zawsze zapisany jako niepotwierdzony;
  - `tytuł modułu - dowód słaby` - tylko tytuł lub cele modułu;
  - `brak dowodu -> orphan`.
  Nigdy nie oznaczaj umiejętności jako uczonej w module wyłącznie na podstawie tytułu modułu bez zapisu `tytuł modułu - dowód słaby`.
- Oczekiwany koszt: kilka wyszukiwań na umiejętność i kilka pobrań na modułu-kandydata, zamiast pobierania wszystkich jednostek wszystkich modułów.

## 9. Pokrycie egzaminu (tabela w części "Co dalej")

Tabela z kolumnami: `Umiejętność (study guide) | Domena | Status | Gdzie`.

- **Tabela jest generowana z `skill-map.md`**, nie utrzymywana osobno: skopiuj wiersze umiejętności, których właścicielem jest ten moduł albo które wskazują gdzie indziej (inny moduł, luka). Przy zmianie przydziału zmienia się mapa, a tabela jest tylko jej widokiem.

- Status: `uczone tutaj`, `uczone w module N`, `luka kursu, opisana osobno`, `tu tylko wzmianka`.
- Kolumna "Gdzie": plik i sekcja (`<plik> §<ID>`) albo URL modułu, gdy pliku jeszcze nie ma.
- Pod tabelą: akapit "Uczciwie o egzaminie" - co ten moduł pokrywa, czego nie, co jeszcze trzeba przerobić.

## 10. Nazwy plików i zgodność z Obsidianem

- Tutorial: `NN-<slug-modułu>.md` (NN = pozycja modułu w kursie; 00 zarezerwowane na plik startowy). Plik luk: `99-luki-egzaminu.md` (lub istniejący `*luki-egzaminu*.md`).
- Źródła: `sources/<slug-modułu>/<unit-id>-<slug>.md` (tak wszędzie: kroki, szablon, znaczniki), inwentarz `sources/<slug-modułu>/_inventory.md`, luki `sources/_gaps/<temat-slug>.md`, dokumentacja uzupełniająca moduł `sources/_docs/<slug>.md`, mapa `sources/_exam/skill-map.md`, pliki pomocnicze (surowy JSON, tymczasowe) `sources/_exam/raw/` - nigdy poza katalogiem wyjściowym.
- Same małe litery, myślniki, bez polskich znaków i spacji w nazwach plików.
- Tylko zwykły Markdown plus `<details>`/`<summary>` i `<sub>`. Bez wtyczek, bez makr, bez składni specyficznej dla jednego edytora, bez diagramów w obcym formacie (rysuj ASCII).
- Nagłówki: `#` = CZĘŚĆ (wielkimi literami, litera i myślnik), `##` = sekcje z ID (`A1.`). Kolejność nigdy nie przeskakuje (A1, A2, A3; nie `A1b`).
- Pliki odsyłają do siebie po nazwie pliku i ID sekcji w znakach `` ` ``.

## 11. Format pliku źródłowego (`sources/`)

Każda zapisana jednostka lub strona dokumentacji zaczyna się od front matter:

```
---
source_url: {pełny URL}
fetched: {RRRR-MM-DD}
tool: {microsoft_docs_fetch | learn-cli | WebFetch | curl}
module: "{tytuł modułu} ({slug})"
unit: "{id-jednostki} - {tytuł jednostki}"
---
```

- Dla jednostki, której nie dało się pobrać (np. interaktywny quiz): `status: not-fetchable` w front matter i krótka notka w treści.
- Dla stron dokumentacji w `sources/_gaps/` i `sources/_docs/` pole `module` zastępuje `topic: "{temat}"`.
- **Jednostki modułu Learn** (`sources/<moduł>/`): treść pod front matter to wierna kopia pobranej strony (nie streszczenie).
- **Strony `_gaps` i `_docs`:** zapisz tylko cytowany fragment (tekst odpowiedniej sekcji), URL i datę pobrania (`fetched`), nie całą stronę. Fragment ma wystarczyć do sprawdzenia cytowanych faktów.
- **Kolejność narzędzi zapisu.** (1) `npx @microsoft/learn-cli fetch <url>` przekierowane do pliku (wierna kopia), jeśli narzędzie jest dostępne (`npx` bywa zablokowany albo niedostępny); (2) w przeciwnym razie `microsoft_docs_fetch` plus Write: to nie jest wierna kopia (MCP może skracać i przekształcać treść), więc wpisz `tool: microsoft_docs_fetch` i wspomnij o tym w raporcie. Dla docs.github.com i README z GitHuba użyj `curl`, jeśli jest dozwolony (API artykułu dokumentacji lub raw.githubusercontent.com), bo WebFetch streszcza treść; w przeciwnym razie WebFetch z `tool: WebFetch`. Wartość `tool:` zawsze odpowiada użytej metodzie.

## 12. Kontrola mechaniczna (krok 12)

Uruchom po napisaniu tutoriala (`T` = plik tutoriala, `<out>` = katalog wyjściowy):

- bloki kodu zbalansowane: liczba linii zaczynających się od trzech odwrotnych apostrofów w `T` jest parzysta (`grep -c '^ *```' T`);
- `<details>` i `</details>` występują tyle samo razy (`grep -c '<details>' T` i `grep -c '</details>' T`);
- brak pozostałości: `grep -nE 'DO USTALENIA|DO DODANIA|TODO|<!--' T` nic nie zwraca (to samo dla `_inventory.md` i pliku luk);
- każdy cytowany `[unit <id>]` ma plik `<out>/sources/<moduł>/<id>-*.md`, a każdy `[docs: URL]` wpis w `sources/_docs` lub `sources/_gaps`;
- wersje i tagi w przykładach zgadzają się z pieczątką wersji (4.6): `grep -nE '@v?[0-9]' T` i porównanie z pieczątką;
- kontrola tokenów inwentarza (sekcja 7);
- nic nie zapisano poza `<out>`: wszystkie pliki zmienione w tym przebiegu leżą w `<out>` (w tym pliki tymczasowe).
