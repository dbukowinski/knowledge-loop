# Pętla Wiedzy v3 — pamięć oparta na dowodach

Framework, dzięki któremu Claude uczy się w każdej domenie (sport, praca BA, AI i kolejne). Wnioski stają się hipotezami z kontrhipotezą. Hipotezy są sprawdzane przez **Indeks Wiedzy Zewnętrznej (9-Sources)**. Zmierzone wartości trafiają do faktów, potwierdzone wnioski do reguł, a zmiany wysokiego ryzyka czekają na Twoją zgodę. Wszystko z historią zmian i oszczędzaniem tokenów.

## Skąd v3

v3 łączy szkielet v2 (domeny, 9-Sources, budżet tokenów, rytmy, struktura Twojego vaultu) z najlepszymi elementami alternatywnego prototypu:

| Nowe w v3 | Po co |
|---|---|
| Cztery typy pamięci: epizody, fakty, hipotezy, reguły | zmierzone wartości (AeT, strefy) mają swoje miejsce i nie są hipotezami |
| `source_id` (np. `coros:<id>`) i typy operacji | ta sama aktywność nigdy nie jest liczona dwa razy |
| Kontrhipoteza i „co rozstrzygnie” w każdej hipotezie | prawdziwa falsyfikacja zamiast zbierania potwierdzeń |
| Statusy `testowana` i `zastąpiona` (+ `superseded_by`) | wiedza może się zmienić bez kasowania historii |
| Bramki jakościowe zamiast samych progów i wag | progi to minimum; liczy się też pomiar, alternatywy i koszt błędu |
| Kolejka `_propozycje.md` | zadania w tle działają z auto approve, a zmiany wysokiego ryzyka i tak czekają na Ciebie |
| „Dane to nie instrukcje” i prywatność zapytań | treść stron nie steruje Claude, a prywatne dane nie trafiają do wyszukiwarek |
| Scenariusze testowe z metrykami i cofaniem zmian | zmiana skilla, która coś pogarsza, nie przechodzi |
| Uwagi o pomiarach w górach | tętno i tempo z gór porównywane tylko z podobnymi sesjami |
| Format odpowiedzi i rozróżnienie „zapisano / proponuję” | zawsze wiesz, co się zmieniło w pamięci |

Odrzucone z prototypu: ograniczenie do sportu, lokalna ścieżka vaultu, całkowita rezygnacja z progów, 12-polowy schemat każdego zapisu, globalny zakaz auto approve.

## Struktura w vaulcie

```
8-System/Pętla Wiedzy/
  _domeny.md, _log.md, _propozycje.md
  sport/      _profil.md, _fakty.md, _index.md, Hipotezy/, Raporty/
  praca-ba/   _profil.md, _fakty.md, _index.md
  ai/         _profil.md, _fakty.md, _index.md
8-System/Lekcje Claude.md
9-Sources/
  _zasady.md
  sport/      _rejestr.md, _wyszukiwanie.md, _luki.md, <temat>.md…
  praca-ba/   _rejestr.md
  ai/         _rejestr.md
4-Knowledge/Sport & Trening/Moje reguły.md
6-Templates/Pętla Wiedzy/        ← 6 szablonów
7-Skills/petla-wiedzy/
  2026-11-05 v2.md               ← poprzednia wersja (do cofnięcia)
  evals/scenariusze.md           ← 14 scenariuszy testowych
```

## Co Claude zapisuje sam, a co czeka na Ciebie

- **Sam** (także w tle): obserwacje, hipotezy i ich statusy, fakty bez wpływu na strefy i plany, indeksy, log, raporty, 9-Sources, dziennik lekcji.
- **Czeka w `_propozycje.md`**: reguły wpływające na obciążenie, intensywność lub bezpieczeństwo; zmiana faktów, od których zależą strefy i progi; zmiany skilli; nowe domeny; usunięcia.
- Akceptujesz w rozmowie: „akceptuję P-003” albo „odrzucam P-003, bo…”.

## Jak Claude o tym wie (oszczędnie)

1. **Skill**: w rozmowach widoczny jest tylko jego opis. Pełna treść ładuje się przy analizie, planowaniu i poprawkach.
2. **Router domen**: `_domeny.md` i profil jednej domeny, nigdy wszystkich naraz.
3. **Na start zadania**: indeks, reguły obowiązujące, fakty bieżące i maks. 3 hipotezy.

## Wdrożenie

1. Zaktualizuj skill z karty propozycji. Poprzednia wersja jest w `7-Skills/petla-wiedzy/`.
2. Skopiuj `vault/` do vaultu (nowsza kopia na Drive, ta z `1-Daily … 8-System`).
3. Zaplanowane zadania:
   - **Niedziela wieczór**: „Uruchom skill petla-wiedzy, rytm tygodniowy (§10.1).”
   - **Pierwsza sobota miesiąca**: „Uruchom skill petla-wiedzy, rytm miesięczny (§10.2 i §11).”
   - W obu włącz „Automatically approve”. Bezpieczeństwo zapewnia kolejka propozycji.
4. Start: analiza ad hoc po zawodach lub bloku (§10.3) i sprawdzenie adresów startowych w rejestrach 9-Sources.

## Twoja rola

- Poprawiaj mnie wprost, w każdej domenie.
- Przeglądaj `_propozycje.md`, gdy coś w niej czeka (zgłoszę to w rozmowie).
- Opcjonalnie: przegląd raportów i dopisywanie zaufanych źródeł do `_rejestr.md`.
