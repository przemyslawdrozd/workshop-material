# Etap 2 — Prompt Engineering dla lepszych wyników

## Cel etapu

- Pokazać, że dobry prompt to specyfikacja zadania
- Nauczyć pracy na kontekście, ograniczeniach i weryfikacji
- Przygotować się do lepszej pracy w Chat i w kolejnych etapach

---

## Dobry prompt to specyfikacja zadania

- Nie pisz tylko: "zrób backend"
- Powiedz, co istnieje i co ma się zmienić
- Określ wynik, ograniczenia i sposób sprawdzenia
- Im mniej domysłów, tym mniej zbędnych iteracji

---

## Struktura dobrego promptu

| Element             | Co doprecyzować?                                        |
| ------------------- | ------------------------------------------------------- |
| Kontekst            | Co budujemy? Jakie pliki, framework i dane są ważne?    |
| Cel                 | Co dokładnie ma się zmienić?                            |
| Kryteria akceptacji | Po czym poznamy, że wynik jest dobry?                   |
| Ograniczenia        | Czego nie ruszać? Jakie biblioteki i wzorce obowiązują? |
| Weryfikacja         | Jakie testy, komendy lub scenariusze uruchomić?         |

---

## Zły prompt vs dobry prompt

**Słaby prompt**

```text
Create backend for bank app.
```

**Lepszy prompt**

```text
Create API endpoints for a Bank Mock System.

Requirements:
- POST /api/accounts, GET /api/accounts, GET /api/accounts/{id}
- validation
- tests
- clear structure
- no authentication yet

Before writing code, propose the file structure and ask if anything is ambiguous.
```

- Dla .NET nazwij ASP.NET Core, DataAnnotations i xUnit
- Dla PHP nazwij Laravel lub Symfony, Form Requests i PHPUnit albo Pest

---

## Skąd brać kontekst?

- zaznaczenie kodu i aktywny plik
- otwarte pliki, importy i nazwy
- README, issue, specyfikacja, przykłady input/output
- referencje typu `#file`, `#selection`, `@workspace`
- nie wrzucaj całego repo, jeśli nie jest potrzebne

---

## Inline vs Chat

- **Inline** — gdy chcesz kontynuacji lokalnego fragmentu
- **Chat** — gdy potrzebujesz planu, wyjaśnienia albo iteracji
- Komentarz w kodzie pomaga przy małym wycinku
- Chat wygrywa przy regułach, edge case'ach i większym zadaniu

---

## Plan first, code later

- Najpierw plan lub propozycja struktury plików
- Potem małe kroki zamiast jednego wielkiego promptu
- Doprecyzowanie niejasności przed implementacją
- Review wyniku przed zaakceptowaniem
