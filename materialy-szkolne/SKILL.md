---
name: materialy-szkolne
description: Tworzenie gotowych promptów do ChatGPT (generator obrazów) na ilustrowane materiały szkolne z matematyki i fizyki – karty pracy, notatki do zeszytu, wersje z lukami, gry planszowe – oraz korekta wygenerowanych obrazów i klucze odpowiedzi. Używaj, gdy użytkownik chce nową kartę pracy, notatkę, grę, prompt dla ChatGPT, sprawdzenie wygenerowanej karty albo pomysł na materiał do sprzedaży (zlotynauczyciel.pl).
---

# Materiały szkolne – prompty do ChatGPT i korekta

Użytkownik jest nauczycielem matematyki (także fizyka). Materiały generuje w ChatGPT (obraz),
sprzedaje na zlotynauczyciel.pl. Najlepiej sprzedają się NOTATKI do zeszytu, potem gry i karty pracy.
ChatGPT robi piękną grafikę, ale myli tekst i liczby – Twoja rola to:
1. wymyślić poprawną merytorycznie treść,
2. dać KOMPLETNY prompt do wklejenia,
3. powiedzieć, który obraz dołączyć jako wzór,
4. dać zweryfikowany klucz odpowiedzi,
5. sprawdzić wygenerowany obraz i dać gotowy prompt poprawkowy.

## Zasady współpracy (ważne)
- ZAWSZE dawaj CAŁY prompt w jednym bloku kodu ````text – nigdy fragmentów typu „dopisz na początku…”.
- Nie zadawaj pytań, jeśli da się przyjąć rozsądne założenie – przyjmij je i napisz jednym zdaniem jakie.
- Zawsze napisz, który obraz dołączyć (pełna ścieżka z folderu `wzory/` albo „obraz poprzedniej strony”).
  Rozróżniaj: ta sama rozmowa w ChatGPT (można odwołać się do „karty wygenerowanej wyżej”, ale
  użytkownik często i tak dołącza obraz – wtedy prompt zaczyna się od „Załączony obraz to…”).
- NIE pisz na materiale, dla której klasy jest (chyba że użytkownik poprosi). Klasę bierz pod uwagę
  tylko przy doborze treści.
- Treść zgodna z polską podstawą programową i polskim zapisem szkolnym:
  - ułamki piętrowe (licznik nad kreską), NIE ukośnik `s/t`,
  - mnożenie `·`, dzielenie `:`, minus `−`, odstęp w liczbach od tysiąca: `1 258`,
  - przecinek dziesiętny: `1,5`.
- Sprawdź kompletność tematu z podstawą programową (np. cechy podzielności: 2, 3, 4, 5, 9, 10, 100).
- KAŻDY wynik przelicz i pokaż tabelę sprawdzenia. Celowo dobieraj „pułapki” (np. 405 dzieli się przez 5,
  ale nie przez 10; 530 parzyste, ale niepodzielne przez 4).
- Klucz odpowiedzi i tabele sprawdzenia podawaj POZA blokiem promptu i ostrzeż, żeby nie wklejać ich do ChatGPT.
- Bądź szczery w ocenie ryzyk (szacunkowo: cały tekst bez błędu za 1. razem ~15–25%, po 2–3 poprawkach ~60–70%).

## Obrazy wzorcowe (folder `wzory/` obok tego pliku)
| Plik | Do czego jako wzór |
|---|---|
| `karta-chomiki-mnozenie-cz1.png` | ilustrowana karta pracy z kratkowanymi polami (najlepsza) |
| `karta-chomiki-mnozenie-cz2.png` | strona 2 karty, panele obok siebie, zadanie z gwiazdką |
| `karta-wyscigowa-predkosc-cz1.png` | karta z ściągą wzorów (ułamki piętrowe) |
| `karta-piracka-pitagoras.png` | ilustrowana karta, jedna strona |
| `notatka-cechy-podzielnosci.png` | NOTATKA – własny styl (białe tło, ramki, ikonki); domyślny wzór notatek |
| `notatka-fizyka-stany-skupienia.png` | notatka ze schematem (trójkąt, kolorowe strzałki) – wzór dla notatek fizycznych/schematów |
| `notatka-fizyka-dynamika-newtona.png` | notatka: 3 ramki (tekst + ilustracja z podpisem), wzór jako ułamek piętrowy, przykład obliczeniowy |
| `notatka-wzor-mnozenie-pisemne.jpg` | notatka „krok po kroku”: numerowane panele, kratki z kolorowymi kolumnami S/D/J (zielona/pomarańczowa/niebieska) – do działań pisemnych |
| `notatka-dzielenie-pisemne.png` | gotowa notatka krok po kroku (3 przykłady, 8 kratkownic); kratki opisywane wiersz po wierszu z „_” = pusta kratka – ta metoda działa |
| `notatka-chemia-mieszaniny.png` | notatka: siatka 2×3 ramek z rysunkami sprzętu laboratoryjnego + kolorowe etykiety kategorii (najbogatsza) |
| `notatka-wzor-mnozenie-przez-10.png` | notatka – dwie kolumny z przykładami |
| `gra-wzor-grzybobranie.png` | gra planszowa – styl plansz/kart (cudzy motyw, nie kopiować grzybów) |
Pełna ścieżka: `C:\Users\PC\.claude\skills\materialy-szkolne\wzory\<plik>`.
Nowe udane materiały dopisuj tu (kopiuj obraz do `wzory/`).

## Stałe bloki do promptów

### Blok: zasady tekstu (wklejaj w każdy prompt)
```
NAJWAŻNIEJSZE ZASADY DOTYCZĄCE TEKSTU:
- Wpisz każdy tekst DOKŁADNIE, słowo w słowo, tak jak podałem w cudzysłowach. Niczego nie zmieniaj, nie skracaj, nie parafrazuj i nie dodawaj od siebie.
- Zachowaj wszystkie polskie znaki (ą ć ę ł ń ó ś ź ż) bez błędów.
- Do całego tekstu zadań użyj prostej, czytelnej czcionki bezszeryfowej, ciemnym kolorem na jasnym tle. Ozdobna czcionka tylko do tytułu głównego i nagłówków.
- Wszystkie liczby, znaki i jednostki wpisz dokładnie jak podano. Nie dodawaj żadnych wyników ani odpowiedzi.
- Pola i linie na odpowiedzi zostaw PUSTE.
- Poza podanym tekstem nie umieszczaj żadnych innych napisów, liter ani cyfr.
- Żaden element graficzny nie może zasłaniać tekstu, liczb ani pól.
```

### Blok: miejsce na obliczenia (karty pracy)
```
NAJWAŻNIEJSZE ZASADY DOTYCZĄCE MIEJSCA NA OBLICZENIA:
- Uczeń pisze obliczenia ręcznie, więc miejsca ma być DUŻO. To ważniejsze niż dekoracje.
- Pola kratkowane (kratka 5 mm), jasne, bez rysunków w środku. [podaj konkretne rozmiary w cm dla każdego zadania]
- Jeśli brakuje miejsca, zmniejsz ilustracje i postacie przy brzegach, ale NIE zmniejszaj pól na obliczenia i nie ściskaj tekstu.
- Panele mają mieć jednolite, jasne, czyste wnętrze.
```

## Szablony

### Karta pracy (ilustrowana, zwykle 2 strony)
- Dziel na 2 strony A4 – mniej tekstu na obraz = mniej błędów, większe pola.
- Strona 1: tytuł „<MOTYW>OWA KARTA PRACY – <TEMAT>”, „(cz. 1)”, „Imię i nazwisko młodego <postać>:”,
  panel ze ściągą/przykładem, 2 zadania. Strona 2: „(cz. 2)”, 2–4 zadania, stopka „Powodzenia, <postać>! Niech … będzie z Tobą!”.
- Zadania stopniowane: rozgrzewka → typowe → pułapki (zera, przeniesienia, jednostki) → „znajdź błąd” → tekstowe → zadanie z gwiazdką.
- Układ pól: przy 4 podpunktach – „cztery kwadratowe pola kratkowane w jednym rzędzie, każde ≥ 4 cm × 4 cm, nad polem litera i działanie, pod polem `= ______`”.
- Jedno zadanie tekstowe = bez podpunktów a)/b).
- Prompt strony 1 zaczyna się:
  „Załączony obraz to WZÓR STYLU I UKŁADU: ilustrowane pergaminowe panele z cieniowanymi ramkami, fioletowe paski tytułowe z ikonami w kółkach, ozdobna stopka, postacie i rekwizyty wystające zza paneli, kolorowe tło. Odtwórz taki sam poziom dopracowania graficznego i podobny układ, ale zmień motyw na <MOTYW> i użyj mojej treści podanej niżej. Nie kopiuj treści ze wzoru. Cały tekst weź wyłącznie z mojej treści poniżej. To jest STRONA 1 z 2 …”
  potem: „Wygeneruj obraz: pionowa strona A4 (proporcje 2:3, wysoka rozdzielczość), temat: …, motyw: … Kolorowa, wesoła ilustracja jak z książki dla dzieci.” + blok zasad tekstu + blok miejsca + „UKŁAD OD GÓRY:” z każdym tekstem w cudzysłowie + „Pamiętaj: …”.
- Prompt strony 2: „Załączony obraz to STRONA 1 z 2 tej karty pracy. Teraz zrób STRONĘ 2 w IDENTYCZNYM stylu…” (dołączyć obraz strony 1) + bloki zasad w całości.

### Notatka do zeszytu (najlepiej się sprzedaje)
- Wzór: `notatka-cechy-podzielnosci.png`. Styl: białe tło, zaokrąglone ramki z kolorowymi nagłówkami, przykłady w ramkach z przerywaną linią, duże liczby, wyróżnione kolorem cyfry, płaskie ikonki (gwiazdka, żarówka, ołówek, zeszyt, mózg-maskotka), pasek „Pamiętaj!” na dole.
- Pionowa 2:3. Szkielet: tytuł → reguły/definicje pogrupowane wg idei (np. „PATRZĘ NA OSTATNIĄ CYFRĘ” / „LICZĘ SUMĘ CYFR”) → przykłady z ✓ (zielony) / ✗ (czerwony) → „UWAGA!” z typowym błędem → „Pamiętaj!”.
- ~60–120 słów; określ precyzyjnie, CO wyróżnić kolorem.
- Zawsze zaproponuj od razu WERSJĘ Z LUKAMI (ta sama rozmowa, dołącz gotową notatkę): reguły z lukami `______`, przy przykładach puste kwadraciki `☐` zamiast ✓/✗, zakaz wpisywania ✓/✗ i rozwiązań, pozostałe teksty bez zmian. Podaj klucz do luk.
- Pakiety: notatka + wersja z lukami + karta pracy/gra z tego samego tematu; wersja A3 plakat.

### Gra planszowa
- Wzór stylu: `gra-wzor-grzybobranie.png` (zakaz grzybów/jesieni, własny unikalny pomysł i motyw).
- Kolejność: plansza (pozioma 3:2, ścieżka ~40 dużych pól, symbole na polach BEZ tekstu, legenda „Pola specjalne:”, START/META) → arkusze kart 12 szt. (3×4, A4, linie cięcia, jedno działanie na kartę, „nie wpisuj wyników”, „żadne nie może zginąć ani się powtórzyć”) → karty graczy → żetony → pionki → instrukcja. Wszystko generować z obrazem planszy jako wzorem.
- Karty z liczbami to największe ryzyko błędów (w prawdziwym produkcie wyszło „8 : 08”). Alternatywa: ChatGPT robi puste ramki kart, a liczby wpisujesz w HTML i składasz arkusz do druku (Chrome headless → PDF).
- Zrealizowany pomysł: „Świąteczne Ubieranie Choinki” (bombka – mnożenie 1 pkt, pierniczek – dzielenie 2, gwiazdka – dwa działania 3; śnieżyca −2 pola, sanie +3; każdy gracz ubiera własną kartę-choinkę z 12 miejscami; pierwszy na mecie dostaje gwiazdę = 2 bombki).

## Korekta wygenerowanego obrazu
Porównaj obraz z promptem punkt po punkcie i zgłoś:
1. brakujące lub zdublowane punkty/zadania (ChatGPT często gubi podpunkt, np. c) albo a)),
2. błędne liczby, znaki działań, jednostki, potęgi (`3²` → `32`), zera (`8 : 08`),
3. literówki i polskie znaki (np. „pałuchy”, „brákującego”),
4. ✓/✗ przy złych liczbach, dopisane wyniki w polach, które miały być puste,
5. wyróżnienia kolorem w złym miejscu lub niekonsekwentne,
6. grafika zasłaniająca tekst/linie (np. stoper na „v = ___”), tekst przy samej krawędzi,
7. pola za małe względem promptu (szacuj: obraz 1024×1536 px ≈ A4, ~5,2 px/mm),
8. zapis niezgodny ze szkolnym (ukośnik zamiast ułamka piętrowego).
Następnie: lista „Zgadza się”, lista „Do poprawy”, i gotowy prompt poprawkowy:
„Popraw tylko <X>, całą resztę <karty/strony/notatki> zostaw bez żadnych zmian (styl, postacie, tło, teksty, układ): …”
Drobiazgi estetyczne oznacz jako opcjonalne. Czytasz obraz w przesłanej rozdzielczości – przy drobnym druku przyznaj niepewność.

## Pomysły w kolejce
- Notatki matematyka: kolejność wykonywania działań (prompt gotowy w historii: schody 4 stopni + przykłady 20 − 3 · 4 = 8, (20 − 3) · 4 = 68, 2 + 3² · 2 = 20, 36 : 6 · 2 = 12, „TAK NIE!” 36 : 12 = 3), o ile więcej / ile razy więcej, zamiana jednostek (schody km–m–cm–mm), rodzaje kątów, liczby rzymskie, pole i obwód prostokąta.
- Fizyka: przemiany stanów skupienia, przedrostki jednostek, prędkość z trójkątem v–s–t, prawo Ohma, ruch jednostajny (karta wyścigowa – istnieje).
