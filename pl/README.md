# Pętla Wiedzy (wersja polska)

Polskie tłumaczenie skilla **Knowledge Loop**: pętli uczenia się dla Claude opartej na dowodach. Claude nie uczy się sam między rozmowami, bo jego wagi się nie zmieniają. Pętla Wiedzy daje mu zewnętrzną pamięć w plikach vaultu (np. Obsidian), dzięki której uczy się w każdej domenie, w której razem pracujecie.

Wnioski z doświadczeń stają się **hipotezami z kontrhipotezą**. Hipotezy są sprawdzane przez **Indeks Wiedzy Zewnętrznej (9-Sources)**. Zmierzone wartości trafiają do **faktów**, potwierdzone wnioski do **reguł**, a zmiany wysokiego ryzyka czekają na Twoją zgodę.

## Zawartość

- `SKILL.md` to skill w wersji polskiej (`petla-wiedzy`). Używa polskich nazw plików w vaulcie (`8-System/Pętla Wiedzy/`, `_domeny.md`, `_profil.md`, `_fakty.md`, `_propozycje.md` itd.).
- Pełna struktura vaultu, szablony i scenariusze testowe są w wersji angielskiej w katalogu `vault/` w głównym folderze repozytorium. Korzystając z polskiego skilla, zmień nazwy plików na polskie odpowiedniki albo dostosuj ścieżki w `SKILL.md`.

Opis działania, zabezpieczeń i podstaw naukowych znajdziesz w głównym [README](../README.md).

## Wdrożenie

1. Zainstaluj `pl/SKILL.md` jako skill w Claude. Nie instaluj jednocześnie wersji angielskiej, bo oba skille by się nakładały.
2. Skopiuj strukturę vaultu i dopasuj nazwy plików oraz profile domen do swoich źródeł danych i metodyk.
3. Utwórz dwa zaplanowane zadania:
   - tygodniowe: „Uruchom skill petla-wiedzy, rytm tygodniowy (§10.1).”
   - miesięczne: „Uruchom skill petla-wiedzy, rytm miesięczny (§10.2 i §11).”

## Licencja

[MIT](../LICENSE)
