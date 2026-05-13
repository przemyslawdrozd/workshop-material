# GitHub Copilot Workshop Material

Kompleksowy zestaw materialow szkoleniowych o GitHub Copilot - od podstaw, przez prompt engineering i bezpieczenstwo, po testowanie, praktyczne scenariusze i przygotowanie do certyfikacji.

## Overview

Repozytorium zawiera uporzadkowane materialy do nauki i prowadzenia warsztatow:

- **szkolenie/** - glowna sciezka warsztatowa krok po kroku
- **study-materials/** - rozszerzone notatki i materialy tematyczne
- **quiz/** - krotkie quizy sprawdzajace wiedze
- **mock-questions/** - testy praktyczne i pytania w stylu certyfikacyjnym
- **project-templates/** - przykladowe projekty do cwiczen z Copilotem
- **materials/** - obrazy i pomocnicze assety do setup guide oraz materialow warsztatowych
- **mcp/** - notatki integracyjne dla workflowow MCP z GitHub Copilot CLI
- **.github/** - konfiguracja Copilot, definicje agentow i skillow

## Repository Structure

### Core workshop path

| Etap | Temat | Plik |
| --- | --- | --- |
| 0 | Start i plan dnia | [szkolenie/etap-0.md](szkolenie/etap-0.md) |
| 1 | Wprowadzenie do GitHub Copilot | [szkolenie/etap-1.md](szkolenie/etap-1.md) |
| 2 | Prompt engineering i praca z kontekstem | [szkolenie/etap-2.md](szkolenie/etap-2.md) |
| 3 | Bezpieczenstwo, prywatnosc i odpowiedzialne AI | [szkolenie/etap-3.md](szkolenie/etap-3.md) |
| 4 | Testowanie i iteracyjna praca z Copilotem | [szkolenie/etap-4.md](szkolenie/etap-4.md) |

### Extended study materials

Materialy z katalogu [study-materials/](study-materials) rozwijaja tematy warsztatowe i nadaja sie do samodzielnej nauki:

- [01-fundamentals.md](study-materials/01-fundamentals.md)
- [02-prompt-engineering.md](study-materials/02-prompt-engineering.md)
- [03-advanced-features.md](study-materials/03-advanced-features.md)
- [04-responsible-ai.md](study-materials/04-responsible-ai.md)
- [05-plans-and-features.md](study-materials/05-plans-and-features.md)
- [06-data-handling.md](study-materials/06-data-handling.md)
- [07-testing-with-copilot.md](study-materials/07-testing-with-copilot.md)
- [08-privacy-fundamentals.md](study-materials/08-privacy-fundamentals.md)
- [09-developer-use-cases.md](study-materials/09-developer-use-cases.md)
- [10-emerging-features-2025.md](study-materials/10-emerging-features-2025.md)
- [quick-reference-cheat-sheet.md](study-materials/quick-reference-cheat-sheet.md)
- [troubleshooting-guide.md](study-materials/troubleshooting-guide.md)

### Knowledge checks

- [quiz/quiz-1.md](quiz/quiz-1.md) - podstawy GitHub Copilot
- [quiz/quiz-2.md](quiz/quiz-2.md) - bezpieczenstwo i dobre praktyki

### Practice tests

- [mock-questions/practice-test-1.md](mock-questions/practice-test-1.md)
- [mock-questions/practice-test-2.md](mock-questions/practice-test-2.md)
- [mock-questions/practice-test-3.md](mock-questions/practice-test-3.md)
- [mock-questions/practice-test-4.md](mock-questions/practice-test-4.md)

### Project templates

Szablony w katalogu [project-templates/](project-templates) pozwalaja cwiczyc z Copilotem na roznych stosach technologicznych:

- [dotnet-web-api](project-templates/dotnet-web-api/README.md)
- [nodejs-api](project-templates/nodejs-api/README.md)
- [python-data-analysis](project-templates/python-data-analysis/README.md)
- [react-native-app](project-templates/react-native-app/README.md)
- [react-todo-app](project-templates/react-todo-app/README.md)

### Workshop assets

Katalog [materials/](materials) zawiera obrazy i pomocnicze assety wykorzystywane w instrukcjach oraz podczas warsztatow.

### Copilot configuration

Plik [AGENTS.md](AGENTS.md) zawiera ogolne wskazowki dla agentow pracujacych w tym repozytorium.

Konfiguracja Copilot i zasoby dla agentow znajduja sie w katalogu [.github/](.github/):

- [.github/copilot-instructions.md](.github/copilot-instructions.md) - instrukcje dla Copilota obowiazujace w calym repozytorium
- `.github/agents/` - definicje niestandardowych agentow (`angular-rest-ui`, `readme-creator`, `scaffolding`, `technical-documentation`)
- `.github/skills/` - wielokrotnie uzywane definicje skillow (`analyze-rest-api-for-angular`, `convert-stitch-design`, `generate-postman-collection`, `plan-angular-ui-from-api`, `pr-description`, `scaffold-angular-feature-ui`, `scaffold-endpoints`)

Integracje MCP opisane sa w katalogu [mcp/](mcp/):

- [mcp/angular/README.md](mcp/angular/README.md) - workflow Stitch + Angular + MCP
- [mcp/gitlab/README.md](mcp/gitlab/README.md) - integracja z GitLab przez MCP i Copilot CLI

## Suggested Learning Paths

### 1. Start from zero

1. Przejdz przez [szkolenie/etap-0.md](szkolenie/etap-0.md) i [szkolenie/etap-1.md](szkolenie/etap-1.md).
2. Nastepnie przeczytaj [study-materials/01-fundamentals.md](study-materials/01-fundamentals.md).
3. Zakoncz pierwszym quizem: [quiz/quiz-1.md](quiz/quiz-1.md).

### 2. Improve prompting and workflow

1. Przejdz przez [szkolenie/etap-2.md](szkolenie/etap-2.md).
2. Uzupelnij material o [study-materials/02-prompt-engineering.md](study-materials/02-prompt-engineering.md) i [study-materials/03-advanced-features.md](study-materials/03-advanced-features.md).
3. Przetestuj podejscie na jednym z projektow z [project-templates/](project-templates).

### 3. Focus on safety and responsible usage

1. Przeczytaj [szkolenie/etap-3.md](szkolenie/etap-3.md).
2. Uzupelnij wiedze przez [study-materials/04-responsible-ai.md](study-materials/04-responsible-ai.md) i [study-materials/08-privacy-fundamentals.md](study-materials/08-privacy-fundamentals.md).
3. Sprawdz wiedze w [quiz/quiz-2.md](quiz/quiz-2.md).

### 4. Practice testing and certification-style work

1. Przejdz przez [szkolenie/etap-4.md](szkolenie/etap-4.md).
2. Przeczytaj [study-materials/07-testing-with-copilot.md](study-materials/07-testing-with-copilot.md).
3. Rozwiaz testy z katalogu [mock-questions/](mock-questions).

## What You Will Learn

- czym GitHub Copilot jest i jak wpisuje sie w codzienny workflow developera
- jak pisac lepsze prompty i dawac modelowi uzyteczny kontekst
- jak korzystac z Copilot Chat, CLI, agentow i przeplywow PR
- jak pracowac odpowiedzialnie z uwzglednieniem prywatnosci, bezpieczenstwa i licencji
- jak traktowac testowanie i weryfikacje jako czesc pracy z AI

## Usage

Mozesz korzystac z repozytorium na kilka sposobow:

- jako z przewodnika do warsztatow prowadzonych krok po kroku
- jako z zestawu materialow do samodzielnej nauki
- jako z bazy pytan do powtorki przed szkoleniem lub certyfikacja
- jako z zestawu projektow treningowych do praktyki z Copilotem

## Contributing

Jesli rozwijasz to repozytorium:

- utrzymuj logiczna strukture katalogow i spojnosc nazewnictwa
- preferuj linki wzgledne do plikow w repozytorium
- aktualizuj README, gdy dodajesz nowa sekcje, quiz, szablon projektu albo agenta/skill
- aktualizuj `.github/copilot-instructions.md`, gdy zmieniasz komendy lub konwencje szablonow
- dbaj o to, by nowe materialy jasno wskazywaly cel i sposob uzycia

## Helpful Links

- [GitHub Copilot](https://github.com/features/copilot)
- [GitHub Docs - Copilot](https://docs.github.com/en/copilot)
- [GitHub Docs - Security](https://docs.github.com/en/code-security)

## Notes

- Materialy sa przygotowane glownie w jezyku polskim.
- Repozytorium laczy tresci warsztatowe, materialy referencyjne i zadania praktyczne.
- Najlepszy efekt daje przechodzenie przez materialy razem z cwiczeniami w projektach szablonowych.
