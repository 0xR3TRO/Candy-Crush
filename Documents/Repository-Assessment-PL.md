# 1. Executive Summary
- Typ projektu: prosta gra przeglądarkowa (HTML/CSS/JS) z assetami obrazów.
- Największe problemy:
  - Rozjazd między dokumentacją (React/Node/Mongo) a stanem repo (brak builda, backendu, zależności).
  - Brak testów, lint/format i automatyzacji jakości.
  - Brak procesu CI/CD oraz polityk bezpieczeństwa i wersjonowania.
  - Płaska struktura plików bez podziału na moduły/odpowiedzialności.
  - Brak informacji o docelowym środowisku uruchomieniowym i utrzymaniowym.
- Największe dźwignie poprawy (top 5):
  1. Uporządkowanie struktury repo i modularizacja kodu gry.
  2. Wprowadzenie build tool + TypeScript + lint/format.
  3. Dodanie testów jednostkowych i e2e dla krytycznych scenariuszy.
  4. CI/CD z quality gates i skanowaniem bezpieczeństwa zależności.
  5. Ustalenie strategii wdrożeń/rollbacku oraz rejestru ryzyk.

# 2. Odczyt repo z samej struktury i dokumentacji
- Co wiadomo na pewno:
  - Repo zawiera `index.html`, `Directories/script.js`, `Directories/style.css` oraz katalog `Media & Images`.
  - Brak plików konfiguracji build/test (np. `package.json`, `Makefile`).
  - README opisuje grę Candy Crush, z założeniem MVC i stackiem React/Node/Mongo.
- Założenia (jawnie):
  - Założenie: gra ma działać w przeglądarce jako aplikacja web (nie natywna).
  - Założenie: brak obecnie produkcyjnego backendu (na podstawie struktury).
  - Założenie: celem jest doprowadzenie repo do poziomu produkcyjnego zespołu webowego.
- Luki informacyjne:
  - Brak informacji o docelowym środowisku (hosting, domena, CDN).
  - Brak informacji o docelowym zakresie funkcji (np. realny leaderboard).
  - Brak informacji o wymaganiach niefunkcjonalnych (SLA, compliance, RTO/RPO).

# 3. Ocena dojrzałości (0–5)
| Obszar | Ocena | Uzasadnienie | Priorytet |
| --- | --- | --- | --- |
| Architektura | 1 | Prosta struktura plików, brak modularizacji. | Wysoki |
| Jakość kodu | 2 | Czytelny JS, ale brak standardów i formatowania. | Wysoki |
| Testy | 0 | Brak infrastruktury testowej. | Wysoki |
| Bezpieczeństwo | 1 | Brak skanów i polityk zależności. | Wysoki |
| CI/CD | 0 | Brak pipeline’ów. | Wysoki |
| Observability | 0 | Brak logowania/monitoringu. | Średni |
| DX | 1 | Brak narzędzi dev (lint, build). | Wysoki |
| Dokumentacja | 2 | README istnieje, ale nie odzwierciedla kodu. | Wysoki |
| Skalowalność | 1 | Brak warstw/kontraktów, brak backendu. | Średni |

# 4. Rekomendowany stack i narzędzia
| Obszar | Obecnie | Rekomendacja | Dlaczego | Koszt zmiany | Ryzyko |
| --- | --- | --- | --- | --- | --- |
| Runtime/framework | HTML/CSS/JS | Wariant A: Vanilla + Vite + TypeScript. Wariant B: React + Vite + TS. | A: minimalna migracja, B: lepsza struktura UI. Kryterium: skala UI/zespołu. | Średni | Niskie/Średnie |
| Testy | Brak | Vitest (unit) + Playwright (e2e) | Krytyczne scenariusze gry i regresje UI. | Średni | Niskie |
| Lint/format | Brak | ESLint + Prettier | Spójność i mniej błędów. | Niski | Niskie |
| Security scanning | Brak | npm audit + GitHub Dependabot + CodeQL | Wczesne wykrycie podatności. | Niski | Niskie |
| CI/CD | Brak | GitHub Actions (lint/test/build/deploy) | Automatyzacja jakości i wdrożeń. | Średni | Niskie |
| Monitoring/logging/tracing | Brak | Sentry (frontend) | Detekcja błędów runtime. | Niski | Niskie |
| IaC / środowiska | Brak | Vercel/Netlify (statycznie) lub Docker + IaC (jeśli backend) | Szybkie wdrożenia i rollback. | Niski/Średni | Średnie |
| Zarządzanie sekretami | Brak | Secrets w GitHub + manager sekretów (np. Doppler) | Bezpieczna konfiguracja. | Niski | Niskie |

Minimalny bezpieczny krok migracyjny: dodać Vite + TS, przenieść `script.js` do `src/`, uruchomić lint/test w CI, a backend/leaderboard rozważyć w osobnej iteracji.

# 5. Docelowa architektura i struktura repo
- Proponowane bounded contexts / moduły:
  - `game-core` (logika planszy, ruchy, kolizje).
  - `score` (punktacja, warunki zwycięstwa).
  - `ui` (render i interakcje).
  - `assets` (obrazy, style).
  - `services` (opcjonalny leaderboard/back-end).
- Kontrakty między modułami:
  - `game-core` udostępnia API: `initBoard`, `swap`, `getMatches`, `step`.
  - `ui` korzysta wyłącznie z publicznych metod `game-core`.
  - `score` konsumuje eventy z `game-core` (np. `onMatch`).
- Docelowe drzewo katalogów (przykładowe):
  - `src/`
    - `game/`
    - `ui/`
    - `score/`
    - `assets/`
    - `index.ts`
  - `tests/`
  - `docs/`
  - `public/`
  - `scripts/`
- Zasady „co gdzie trafia”:
  - Logika gry wyłącznie w `src/game`.
  - UI i DOM w `src/ui`.
  - Assety tylko w `public`/`assets`.

# 6. Proces wytwarzania end-to-end
- Git workflow i standard PR:
  - `main` + krótkie feature branche (`feat/*`, `fix/*`).
  - PR: opis zmian, checklist, link do issue.
- Definition of Ready / Definition of Done:
  - DoR: opis wymagań + kryteria akceptacji.
  - DoD: testy zielone, lint OK, aktualizacja docs.
- Quality gates przed mergem:
  - Lint + unit + e2e + CodeQL + skan zależności.
- Wersjonowanie i release strategy:
  - SemVer + changelog automatyczny (np. Release Please).
- Plan rollback i hotfix:
  - Rollback przez rollback deployu (Vercel/Netlify) lub tag Docker.
  - Hotfix: osobny branch `hotfix/*` z priorytetowym deployem.

# 7. Plan wdrożenia (30-60-90)
| Faza | Zadania | Owner (rola) | Zależności | Ryzyko | Kryterium ukończenia |
| --- | --- | --- | --- | --- | --- |
| 0–30 | Uporządkowanie struktury repo, Vite+TS, ESLint/Prettier | Tech Lead | brak | Niskie | Build działa lokalnie i w CI |
| 31–60 | Unit testy logiki + Playwright e2e, CI gates | QA/Dev | Faza 0–30 | Średnie | Testy krytyczne przechodzą |
| 61–90 | Wdrożenie deployu + monitoring, decyzja o backendzie | DevOps/Lead | Faza 31–60 | Średnie | Stabilny deploy + alerting |

Quick Wins (1–2 tyg.):
- Ujednolicenie dokumentacji (README ↔ stan kodu).
- Dodanie ESLint/Prettier oraz prostego CI.

# 8. Rejestr ryzyk i mitigacje
| Ryzyko | Prawdopodobieństwo | Wpływ | Mitigacja | Trigger |
| --- | --- | --- | --- | --- |
| Rozjazd wymagań z dokumentacją | Wysokie | Średni | Aktualizacja README + ADR | PR z dużą zmianą zakresu |
| Brak testów regresyjnych | Wysokie | Wysoki | Minimalne unit + e2e | Błąd produkcyjny |
| Zbyt szybka rozbudowa stacku | Średnie | Średni | Wariant A (minimalny) jako krok 1 | Opóźnienia w dostawie |
| Brak decyzji o backendzie | Średnie | Średni | 2–3 warianty z kryteriami wyboru | Konflikt wymagań |

# 9. Backlog techniczny (priorytetyzowany)
**P0**
- Zsynchronizować README z realnym stanem repo (S). Efekt: jasność scope’u i stacku.
- Dodać Vite + TS + ESLint/Prettier + CI (M). Efekt: stabilny build i jakość.

**P1**
- Pokryć logikę gry testami jednostkowymi (M). Efekt: mniej regresji.
- Dodać e2e (Playwright) dla kluczowych scenariuszy (M). Efekt: stabilność UI.

**P2**
- Decyzja o leaderboardzie: localStorage vs. backend (S). Efekt: jasny kierunek produktu.
- Monitoring błędów w przeglądarce (S). Efekt: szybsza reakcja na błędy.

# 10. Metryki sukcesu
- Bazowe KPI + targety:
  - DORA: Lead Time < 1 dzień, Deployment Frequency ≥ 1/tydz., Change Fail Rate < 10%, MTTR < 4h.
  - Jakość: pokrycie unit > 60% (po 90 dniach), 0 krytycznych podatności.
  - Niezawodność: 0 blokujących regresji UI na release.
- Jak mierzyć postęp co sprint:
  - CI raportuje test coverage i czas pipeline.
  - Release notes + liczba bugów z produkcji.
