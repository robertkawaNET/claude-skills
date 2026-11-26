# Szablon tutoriala modułu

Szkielet pliku `NN-<slug-modułu>.md` oraz pliku luk. Formaty szczegółowe (znaczniki źródeł, flaga błędu, quiz, pytania kontrolne, cross-ref, pieczątka wersji, blok ćwiczenia, standard luk) są w `style-guide-pl.md` i nie są tu powtarzane; ten plik pokazuje tylko układ. Wszystko w `{...}` to miejsce do uzupełnienia. Bloki oznaczone "PRZYKŁAD" to przykłady, nie domyślne wartości: dobierz technologię do produktu modułu.

Zasady układu:

- Części są literowane po kolei: `# CZĘŚĆ A - ...`, `# CZĘŚĆ B - ...` itd. Liczba części teorii wynika z treści modułu. Każda część ma co najmniej jedną sekcję `##` z ID `A1.`, `A2.`... Numeracja w części idzie 1..n bez przerw i bez sufiksów.
- Część A to zawsze "co to jest i jak działa".
- Każda sekcja `##` w częściach teorii zaczyna się od linii `_Źródło: ..._` (patrz `style-guide-pl.md`, znaczniki źródeł; reguła dla ćwiczeń, quizu i pytań kontrolnych jest tam).
- Nic w treści nie zależy od sesji ani od pliku spoza `<out>`.
- Po wypełnieniu usuń wszystkie komentarze HTML oraz ten fragment od początku pliku szablonu do linii `<!-- KONIEC-ZASAD-SZABLONU -->` (ta linia to marker: w gotowym pliku nie może zostać ani ona, ani żaden `<!--`).
- Ćwiczenia, gdy moduł nie ma jednostki ćwiczeniowej: patrz `style-guide-pl.md`, "Blok ćwiczenia".
- Sekcja, której cały materiał pochodzi z jednej jednostki, ma tylko linię `_Źródło:_` (bez powtórzeń w treści). "Sprzątanie" może być jedną krótką linią `brak`, gdy nic nie powstało.

<!-- KONIEC-ZASAD-SZABLONU -->

---

# Plik tutoriala

```markdown
# Moduł {NN}: {polski tytuł tematu} ({lista głównych pojęć})

Moduł Microsoft Learn: **{tytuł modułu po angielsku}** - {URL modułu}
Cel: po tym module {co student rozumie i umie zrobić, jedno zdanie}.
Czas: ok. {X-Y} h, orientacyjnie (z czasów jednostek modułu i liczby ćwiczeń, nie z zgadywania). {Wymagania wstępne i środowisko; gdzie robić ćwiczenia}. {Koszt: "Żadne ćwiczenie nie tworzy płatnych zasobów" albo lista kosztów z odsyłaczem do ćwiczeń}.

{Jedna linia legendy: nazwy znaczników i odsyłacz do pełnej legendy, wg style-guide-pl.md sekcja 3 ("Legenda tylko tutaj"); nie kopiuj pełnej legendy}
{Jedno zdanie o odwołaniach "moduł N", jeśli są używane (style-guide-pl.md, cross-ref)}

---

# CZĘŚĆ A - CO TO JEST I JAK TO DZIAŁA

## A1. {Czym jest {produkt/pojęcie}}
_Źródło: {znacznik wg style-guide-pl.md}_

{Wyjaśnienie prostym językiem; każdy termin angielski objaśniony przy pierwszym użyciu.}

## A2. {Po co to wszystko (kontekst z modułu)}
_Źródło: {znacznik}_

{Treść. Tabela, drzewko ASCII lub kod z numerowanymi komentarzami (1)..(n) i listą "Objaśnienie:" pod spodem.}

{Rzecz, o którą pytają na egzaminie, jako krótka fraza w tekście lub w nagłówku sekcji, np. "(egzamin je lubi)"; blockquote `> **Egzamin je lubi:**` jest tylko w pliku luk.}

---

# CZĘŚĆ B - {TEMAT}

## B1. {Sekcja}
_Źródło: {znacznik}_

{Treść.}

{... kolejne części C, D, ... zgodnie z treścią modułu ...}

---

# CZĘŚĆ {X} - ĆWICZENIA

({Jedno zdanie wstępu: co przeczytać wcześniej, jak zapisywać postęp i wyniki, że każde ćwiczenie ma ten sam układ pól wg style-guide-pl.md. Jeśli żadne ćwiczenie nie tworzy płatnych zasobów, napisz to tutaj.})

{Powtórz blok ćwiczenia z przykładów poniżej dla każdego ćwiczenia I1, I2, ... Każde ćwiczenie pokrywa wskazane sekcje teorii i nie odwołuje się do późniejszych.}

---

# CZĘŚĆ {Y} - QUIZ Z MODUŁU MICROSOFTU ({N} pytań) + wyjaśnienia

{Jedna sekcja `##` na pytanie, format i marker wnioskowania wg style-guide-pl.md 4.2. Przy wielu pytaniach: jedno zdanie o wnioskowaniu odpowiedzi tutaj, a przy pytaniach krótki znacznik.}

## {Y}1. {Pytanie w skrócie}
-> *{poprawna odpowiedź}* {pułapki}. {marker odpowiedzi wnioskowanej, jeśli źródło jej nie pokazuje}

{WARIANT, gdy Learn nie udostępnia pytań: zamiast powyższej części użyj części o tytule "QUIZ (pytania autorskie - Learn nie udostępnia pytań modułu)" i formatu z style-guide-pl.md "Quiz autorski"; każde pytanie ma w linii źródła znacznik `[autor]`.}

---

# CZĘŚĆ {Z} - PYTANIA KONTROLNE (odpowiedz bez zaglądania)

{tyle pytań, ile moduł uczy (5-12), bez dopełniania podobnymi; każde jako `##` z odpowiedzią w `<details>`; format wg style-guide-pl.md "Pytania kontrolne".}

## {Z}1. {Pytanie}
<details><summary>Odpowiedź</summary>

{Odpowiedź.}
</details>

---

# CZĘŚĆ {W} - CO DALEJ

## {W}1. Następny krok i pokrycie egzaminu
_Źródło: {znacznik}_

{Co dalej: następny moduł kursu i kiedy wrócić do którego fragmentu.}

**Pokrycie egzaminu** (tabela jest generowana z `sources/_exam/skill-map.md`: skopiuj wiersze umiejętności tego modułu i tych, które wskazują gdzie indziej; nie prowadź jej osobno, style-guide-pl.md sekcja 9) - {tematy z obszaru tego modułu, które lista umiejętności egzaminu ({stan z daty {RRRR-MM}}) wymienia, a które nie są uczone w tym pliku}:

| Umiejętność (study guide) | Domena | Status | Gdzie |
|---|---|---|---|
| {umiejętność} | {N} | {status wg style-guide-pl.md} | {plik §ID albo URL modułu} |

## {W}2. Uczciwie o egzaminie
{Co ten moduł pokrywa, czego nie, jakie pliki jeszcze przerobić.}
```

---

# Plik luk egzaminu (szablon)

Nazwa: `<out>/99-luki-egzaminu.md` albo istniejący plik pasujący do `*luki-egzaminu*.md` (kontynuuj jego numerację). Tworzony tylko, gdy jest orphan; nigdy pusty ani szkieletowy. Standard sekcji: `style-guide-pl.md`, "Standard pliku luk".

````markdown
# Luki egzaminu {KOD EGZAMINU} (tematy spoza modułów Microsoftu)

## {NN}.{n} {Temat} (domena {N})
_Źródło: [docs: {URL}]_

**Co to jest.** {Wyjaśnienie prostym językiem.}

**Po co.** {Dlaczego jest ważne i co się psuje bez tego.}

**Jak tego używać.** {Kroki lub zasada użycia.}

**Minimalny przykład.**
```{język}
{najmniejszy działający przykład}
```

> **Egzamin je lubi:**
> - {pułapka lub wartość do zapamiętania}

{... kolejne sekcje {NN}.{n+1}, ... wstawiane przed "Samoocena", numeracja ciągła ...}

## Samoocena
{Jedno zdanie: jeśli umiesz bez zaglądania napisać {lista rzeczy do napisania z pamięci}, jesteś blisko zdania. Odsyłacz do study guide: {URL study guide}.}
````

---

# Przykłady wypełnionych bloków ćwiczenia

Trzy PRZYKŁADY (nie domyślne wartości) pokazują, jak ten sam blok wygląda dla różnych produktów. Układ pól i zasady: `style-guide-pl.md`, "Blok ćwiczenia". Wybierz wariant pasujący do produktu modułu albo napisz własny.

## PRZYKŁAD 1 - plik konfiguracyjny (GitHub YAML)

````markdown
## I1. Hello workflow - eventy i kontekst

**Gdzie / Plik:** `.github/workflows/hello.yml`
```yaml
name: Hello
on:
  push:
  workflow_dispatch:
jobs:
  hello:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@{wersja}
      - name: Kontekst
        run: echo "event: ${{ github.event_name }}"
      - name: Lista plików
        run: ls -la
```
**Zadania:** (a) po `push` otwórz run i rozwiń każdy krok; (b) uruchom ręcznie **Run workflow**; (c) usuń krok `checkout` i zobacz, że `ls` nie pokazuje plików repo.

**Sprawdź:** (a) każdy krok ma własny zielony fragment logu; (b) w logu jest `event: workflow_dispatch`; (c) bez `checkout` katalog roboczy jest pusty.

**Sprzątanie:** przywróć krok `checkout`. Poza tym brak - nic płatnego nie powstało.
````

## PRZYKŁAD 2 - Azure CLI z kosztem i sprzątaniem

````markdown
## I2. Konto magazynu przez Azure CLI

**Gdzie / Plik:** Cloud Shell (Bash)
```bash
az group create --name rg-{moduł}-i2 --location {region}           # (1)
az storage account create --name {unikalna-nazwa} \
  --resource-group rg-{moduł}-i2 --sku Standard_LRS                # (2)
az storage account show --name {unikalna-nazwa} \
  --resource-group rg-{moduł}-i2 --query sku.name                  # (3)
```
Objaśnienie: (1) grupa zasobów na to jedno ćwiczenie, żeby sprzątanie było jedną komendą; (2) najtańszy rodzaj replikacji (LRS = trzy kopie w jednym centrum danych); (3) odczyt SKU do sprawdzenia.

**Koszt:** {SKU, orientacyjna cena za GB/miesiąc, informacja o darmowym progu i jego limicie czasowym}. Przy kilku minutach pracy koszt jest pomijalny, o ile wykonasz Sprzątanie.

**Zadania:** (a) utwórz konto i odczytaj SKU; (b) spróbuj utworzyć drugie konto o tej samej nazwie i przeczytaj błąd.

**Sprawdź:** (a) komenda `show` wypisuje `"Standard_LRS"`; (b) błąd mówi, że nazwa jest już zajęta (nazwy kont są globalnie unikalne).

**Sprzątanie:**
```bash
az group delete --name rg-{moduł}-i2 --yes --no-wait
az group exists --name rg-{moduł}-i2   # po minucie powinno wypisać false
```
````

## PRZYKŁAD 3 - portal (click-path)

````markdown
## I3. Sieć wirtualna w portalu

**Gdzie / Plik:** Portal: Resource groups -> + Create

1. Resource groups -> **+ Create** -> Subscription: {subskrypcja}, Resource group: `rg-{moduł}-i3`, Region: {region} -> **Review + create** -> **Create**.
2. Na pasku wyszukiwania wpisz **Virtual networks** -> **+ Create**.
3. Na karcie Basics wybierz grupę `rg-{moduł}-i3`, w polu Name wpisz `vnet-{moduł}`, Region jak w kroku 1.
4. Karta IP addresses: zostaw domyślną przestrzeń adresową i podsieć `default`.
5. **Review + create** -> **Create** i poczekaj na komunikat **Your deployment is complete**.

**Koszt:** {sieć wirtualna sama nie jest naliczana; napisz, które dodatki (np. publiczny adres IP, bramka) kosztują, albo "brak kosztu - <powód>"}.

**Zadania:** (a) otwórz zasób i odczytaj przestrzeń adresową; (b) spróbuj dodać drugą podsieć z adresami nakładającymi się na `default` i przeczytaj błąd.

**Sprawdź:** (a) w Overview widać przestrzeń adresową z kroku 4; (b) portal odrzuca podsieć z komunikatem o nakładaniu się zakresów.

**Sprzątanie:** Resource groups -> `rg-{moduł}-i3` -> **Delete resource group** -> wpisz nazwę grupy -> **Delete**. Sprawdź, że grupa zniknęła z listy.
````
