# Pętla Wiedzy (wersja polska)

Polskie tłumaczenie skilla **Knowledge Loop**: pętli uczenia się dla Claude opartej na dowodach. Claude nie uczy się sam między rozmowami, bo jego wagi się nie zmieniają. Pętla Wiedzy daje mu zewnętrzną pamięć w plikach vaultu (np. Obsidian), dzięki której uczy się w każdej domenie, w której razem pracujecie.

Wnioski z doświadczeń stają się **hipotezami z kontrhipotezą**. Hipotezy są sprawdzane przez **Indeks Wiedzy Zewnętrznej** (`sources/`). Zmierzone wartości trafiają do **faktów**, potwierdzone wnioski do **reguł**, a zmiany wysokiego ryzyka czekają na Twoją zgodę.

## Zawartość

- `SKILL.md` to skill w wersji polskiej (`petla-wiedzy`). Ma polskie instrukcje, ale korzysta z **tej samej struktury plików** co wersja angielska: jednego folderu `Knowledge Loop/` z katalogu `vault/` repozytorium.
- Opis działania, zabezpieczeń, inspiracji (metoda bazy wiedzy LLM Karpathy'ego, układ vaultu Super Brain) oraz tabelę mapowania na numerowany vault znajdziesz w głównym [README](../README.md).

## Wdrożenie

1. Zainstaluj `pl/SKILL.md` jako skill w Claude. Nie instaluj jednocześnie wersji angielskiej, bo oba skille by się nakładały.
2. Skopiuj `vault/Knowledge Loop/` w dowolne miejsce vaultu i dopasuj profile domen do swoich źródeł danych i metodyk.
3. Utwórz dwa zaplanowane zadania:
   - tygodniowe: „Uruchom skill petla-wiedzy, rytm tygodniowy (§10.1).”
   - miesięczne: „Uruchom skill petla-wiedzy, rytm miesięczny (§10.2 i §11).”

## Licencja

[MIT](../LICENSE)
