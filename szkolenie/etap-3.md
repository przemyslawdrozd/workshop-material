# Etap 3 — Odpowiedzialna sztuczna inteligencja, prywatność i bezpieczeństwo

## Cel etapu

- Korzystać z Copilota bezpiecznie i świadomie
- Rozumieć dane, licencje i ryzyka
- Wprowadzić prosty quality gate dla kodu AI

---

## Co Copilot wysyła na GitHub?

- Do działania potrzebuje kontekstu zadania
- To nie znaczy, że zbiera kompletne pliki źródłowe jako telemetrię
- W środowisku firmowym liczą się privacy controls i auditability
- Zasada: dawaj tylko potrzebny kontekst

---

## Wrażliwe dane

- sekrety, connection stringi, tokeny, dane osobowe
- nie akceptuj hardcoded secrets
- używaj env vars i secret stores
- dla proprietary logic stosuj exclusions, gdy trzeba

---

## Licencje i odpowiedzialność

- public code suggestions mogą przypominać publiczny kod
- sprawdzaj license compatibility
- zaakceptowany kod staje się Twoją odpowiedzialnością
- open source wymaga tego samego review

---

## Bezpieczne używanie Copilota

- rozumiej kod przed wdrożeniem
- security-sensitive code = głębszy review i testy
- content filtering pomaga, ale nie zastępuje człowieka
- AI wspiera decyzję, nie przejmuje odpowiedzialności

---

## Review i quality gates

- review diffu
- testy happy path i negative path
- lint / static analysis / code scanning
- secrets scan i kontrola ekspozycji danych

---

## MCP i agenci = większa powierzchnia ryzyka

- model dostaje dostęp do narzędzi i akcji
- dawaj minimalne uprawnienia
- ustawiaj jasne granice i zatwierdzenia
- monitoruj skutki uboczne i logi
