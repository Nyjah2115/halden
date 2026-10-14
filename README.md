# Halden® — strona do nagrania rolki

Wersja zegarkowa strony Solen®. Otwórz `index.html` w Chrome lub Safari, włącz pełny ekran i scrolluj.

## Skróty
- **A**: auto-scroll przez całą stronę (ok. 16 s, równe tempo, najlepszy do nagrywania). Ponowne A zatrzymuje, kółko myszy też.
- **C**: ukryj / pokaż kursor.
- **0**: powrót na górę.

## Co jest czym
- `frames/hero/`: klatki wideo hero, kamera jedzie od kucającego mężczyzny do zbliżenia na zegarek (Kling 3.0, OpenArt).
- `frames/product/`: klatki obrotu zegarka: tarcza → bok z koronką → dekiel → z powrotem do tarczy (Veo 3.1, OpenArt,
  bez dźwięku; ta sama klatka na start i koniec, więc obrót kończy się dokładnie na tarczy pod ceną).
- `frames/watch-mask.png`: wycięty zegarek z pierwszej klatki obrotu (Vision na Macu), maska na czas przejścia.
- `frames/manifest.js`: liczba klatek + krzywa ruchu obrotu (równe tempo przy scrollu).
- `source/`: oryginały z OpenArt (obrazy GPT Image 2 + oba wideo .mp4); `source/old/` to pierwsza próba obrotu
  (czysty tylko do połowy, potem przenikanie zamiast obrotu).

## Przejście (jak w Solen)
1. Hero kończy się zbliżeniem na nadgarstek, tarcza na środku kadru.
2. Mężczyzna się rozmywa, tło zostaje jasne.
3. Ostry zegarek produktowy pojawia się dokładnie na jego zegarku (maska `watch-mask.png`, wyrównanie w `MATCH`).
   Zegarek jest ciemny, więc tryb `screen` z Solen by go zgubił; stąd maska zamiast mieszania.
4. Tło gaśnie do czerni, maska znika, zegarek rośnie i zaczyna się obracać.
5. Opis szkła przy widoku tarczy, opis tytanowej koperty przy boku i deklu, „Chrono 01” z ceną, gdy tarcza wraca na wprost.

## Płynność obrotu
- Klatki są przenikane (przy scrollu nie ma przeskoków między klatkami).
- Scroll jest rozłożony równo na ruch, nie na czas wideo, więc obrót ma stałe tempo.

## Strojenie (w `index.html`)
- `.track { height: 900vh }`: długość scrolla (więcej = wolniej).
- `T = { ... }`: kiedy gra hero, kiedy jest „fade”, kiedy obraca się produkt.
- `data-in` / `data-out` na `.callout`: kiedy pojawiają się teksty.
- `AUTO_SECONDS`: czas auto-scrolla.
