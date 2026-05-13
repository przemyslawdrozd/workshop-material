# Etap 4 — Copilot CLI, agenci i testowalny workflow

## Cel etapu

- Przejść od pracy w IDE do pracy agentowej w terminalu
- Pokazać Copilot CLI jako praktyczny interfejs do repo
- Utrwalić workflow: plan -> implementacja -> testy -> review
- Zrozumieć, gdzie pasują custom agents, skills i MCP

---

## Jak ten etap spina poprzednie?

| Etap | Co bierzemy dalej?                            |
| ---- | --------------------------------------------- |
| 1    | Copilot to platforma, nie tylko autocomplete  |
| 2    | Dobry prompt = kontekst, cel i kryteria       |
| 3    | AI wymaga granic, review i kontroli uprawnień |
| 4    | CLI + agenci + testy jako realny workflow     |

---

## Copilot CLI — po co?

- Praca z Copilotem bez wychodzenia z terminala
- Analiza repo, zmiany w plikach, testy i debugowanie
- Interakcja z GitHubem/Gitlabem: issues, PR, Actions
- Dobre miejsce na większe, wieloetapowe zadania

---

## Start pracy w CLI

```shell
copilot
```

- uruchamiaj w katalogu projektu
- potwierdź zaufany katalog
- zaloguj się przez `/login`, jeśli trzeba
- dodawaj pliki do kontekstu przez `@path/to/file`
- uruchamiaj shell bez modelu przez `!command`

---

## Interaktywnie i programmatycznie

**Tryb interaktywny**

```shell
copilot
```

**Jednorazowy prompt**

```shell
copilot -p "Analyze the test failures and suggest fixes"
```

- interaktywnie: rozmowa, iteracja, sterowanie pracą
- programmatycznie: szybkie zadania i automatyzacja

---

## Podstawowe komendy

| Obszar   | Komendy                                            |
| -------- | -------------------------------------------------- |
| Model    | `/model`                                           |
| Sesja    | `/resume`, `/session`, `/rename`, `/new`, `/clear` |
| Kontekst | `/context`, `/usage`, `/compact`                   |
| Katalogi | `/cwd`, `/add-dir`, `/list-dirs`                   |
| Kod      | `/diff`, `/review`, `/tasks`                       |
| Pomoc    | `/help`                                            |

---

## Kontekst w CLI

| Sytuacja              | Komenda / mechanizm | Po co?                                     |
| --------------------- | ------------------- | ------------------------------------------ |
| Dodać plik do promptu | `@path/to/file`     | precyzyjny kontekst bez wklejania treści   |
| Zmienić katalog pracy | `/cwd`              | praca na innym projekcie bez restartu      |
| Dodać katalog         | `/add-dir`          | kontrolowany dostęp poza bieżącym folderem |
| Sprawdzić dostęp      | `/list-dirs`        | lista katalogów dopuszczonych do pracy     |

---

## Context, usage, compact

| Komenda    | Kiedy użyć?                                            | Co daje?                                |
| ---------- | ------------------------------------------------------ | --------------------------------------- |
| `/context` | gdy odpowiedzi tracą kontekst albo zadanie jest długie | podgląd zużycia okna kontekstu          |
| `/usage`   | gdy chcesz zobaczyć statystyki sesji                   | requesty, czas sesji, tokeny, modele    |
| `/compact` | gdy rozmowa robi się długa                             | kompresuje historię i odzyskuje miejsce |

---

## Tryby pracy i modele

- domyślnie: ask/execute mode
- planowanie przed kodem: `Shift+Tab` -> plan mode
- dobór modelu: `/model`
- prostsze zadania: szybszy model
- analiza, architektura, większe zmiany: mocniejszy model

---

## Testowanie jako oś praktyczna

- testy pokazują, czy agent naprawdę dowiózł wynik
- failure jest informacją zwrotną dla kolejnego promptu
- edge cases trzeba dopowiadać świadomie
- negative paths są częścią jakości, nie dodatkiem

```text
Write tests for edge cases: empty input, negative amounts, non-existent account.
Use Given/When/Then structure.
```

---

## Review before fix

- nie poprawiaj w ciemno
- najpierw poproś o analizę
- oddziel diagnozę od implementacji
- zatwierdzaj tylko potwierdzone zmiany

```text
Review the generated code. Find missing validation, edge cases, security issues,
and test gaps. Do not change files yet. Return a prioritized list.
```

---

## Skills

- skill = instrukcje + opcjonalne skrypty + zasoby
- każdy skill ma własny `SKILL.md`
- Copilot ładuje skill wtedy, gdy pasuje do zadania
- dobre do powtarzalnych procedur zespołu

---

## Komendy skills

| Komenda          | Po co?                        |
| ---------------- | ----------------------------- |
| `/skills list`   | lista dostępnych skills       |
| `/skills info`   | szczegóły i lokalizacja skill |
| `/skills reload` | przeładowanie po dodaniu      |
| `/skills add`    | dodanie lokalizacji skills    |

---

## Custom agents

- wyspecjalizowane wersje Copilota do konkretnych zadań
- działają w osobnym kontekście jako subagenci
- mogą mieć własne instrukcje, narzędzia i MCP
- dobre do review, researchu, refaktoryzacji, dokumentacji

---

## Built-in agents w CLI

| Agent           | Do czego?                     |
| --------------- | ----------------------------- |
| task            | testy, buildy, lint, komendy  |
| general-purpose | większe zadania wieloetapowe  |
| code-review     | review realnych problemów     |
| research        | głębsze badanie z cytowaniami |

---

## Własne custom agents

- profile agentów to pliki Markdown `.agent.md`
- lokalizacje: projekt albo katalog użytkownika
- użycie przez `/agent`, prompt lub `--agent`

```shell
copilot --agent security-auditor --prompt "Review src for security issues"
```

---

## MCP

- Model Context Protocol = standard podłączania narzędzi i danych
- GitHub MCP jest dostępny domyślnie w Copilot CLI
- dodatkowe serwery można dodać przez `/mcp add`
- MCP zwiększa możliwości, ale też powierzchnię ryzyka

---

## Zasady dla MCP i agentów

- minimalne potrzebne uprawnienia
- tylko zaufane katalogi i serwery
- review narzędzi zanim dasz dostęp
- ostrożnie z automatycznymi zgodami
- nie testuj integracji na produkcji

---

## Demo: Bank Mock System

1. CLI: zapytaj o plan małej zmiany
2. Agent: przygotuj implementację
3. Terminal: uruchom aplikacje
4. CLI: przeanalizuj failure
5. Review: sprawdź diff i ryzyka
6. Iteracja: popraw tylko potwierdzone problemy

---

## Linki do dokumentacji

- Quickstart: https://docs.github.com/en/copilot/get-started/quickstart
- About Copilot CLI: https://docs.github.com/en/copilot/concepts/agents/about-copilot-cli
- Using Copilot CLI: https://docs.github.com/en/copilot/how-tos/use-copilot-agents/use-copilot-cli
- Custom agents: https://docs.github.com/en/copilot/concepts/agents/copilot-cli/about-custom-agents
- Skills: https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills
- MCP: https://docs.github.com/en/copilot/concepts/agents/cloud-agent/mcp-and-cloud-agent
