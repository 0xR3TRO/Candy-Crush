## Opis projektu

### Cel:

Projekt "Candy Crush w przeglądarce" ma na celu stworzenie gry w przeglądarce internetowej, bazującej na kultowej grze Candy Crush. Aplikacja umożliwi graczom zabawę w dopasowywanie kolorowych cukierków w celu zdobywania punktów i przechodzenia przez różnorodne poziomy. Gra będzie dostępna na różnych urządzeniach, zapewniając płynną i angażującą rozgrywkę.

### Opis funkcji:

- **Rozgrywka:** Gracze będą przesuwać cukierki, aby tworzyć linie składające się z co najmniej trzech identycznych cukierków, zdobywając w ten sposób punkty.
- **Poziomy:** Gra będzie posiadać wiele poziomów o rosnącym stopniu trudności.
- **Bonusy:** Specjalne cukierki i bonusy za tworzenie większych kombinacji lub realizację określonych celów.
- **Tablica wyników:** Gracze będą mogli porównywać swoje wyniki z wynikami znajomych i innych graczy.
- **Integracja społecznościowa:** Możliwość udostępniania wyników i zapraszania znajomych do gry przez media społecznościowe.

## Analiza wymagań:

### Wymagania funkcjonalne:

- **Rozgrywka:** Intuicyjny interfejs umożliwiający przesuwanie cukierków w celu tworzenia linii identycznych cukierków.
- **Poziomy:** Wielopoziomowa struktura gry z rosnącym stopniem trudności.
- **Bonusy:** Mechanizmy tworzenia i wykorzystywania specjalnych cukierków.
- **Tablica wyników:** Funkcja porównywania wyników z innymi graczami.
- **Integracja społecznościowa:** Opcje udostępniania wyników i zapraszania znajomych.

### Wymagania niefunkcjonalne:

- **Płynność rozgrywki:** Gra powinna działać płynnie na różnych przeglądarkach i urządzeniach.
- **Estetyka:** Kolorowa i atrakcyjna grafika nawiązująca do oryginalnej gry Candy Crush.
- **Interfejs użytkownika:** Intuicyjny i łatwy w obsłudze interfejs.

## Projekt interfejsu:

### Szkice/wizualizacje interfejsu:

- _Strona główna:_ Menu główne z opcjami rozpoczęcia gry, przeglądania poziomów, tablicy wyników i ustawień.
- _Ekran gry:_ Plansza do gry z cukierkami, licznik punktów, licznik ruchów, pasek postępu poziomu.
- _Tablica wyników:_ Lista wyników graczy, możliwość filtrowania według znajomych i globalnych graczy.

### Mapa strony:

- _Strona główna_
  - Menu główne
  - Opcje rozpoczęcia gry
  - Tablica wyników
  - Ustawienia
- _Ekran gry_
  - Plansza do gry
  - Licznik punktów
  - Licznik ruchów
  - Pasek postępu poziomu
- _Tablica wyników_
  - Wyniki znajomych
  - Wyniki globalne

## Architektura systemu:

### Opis struktury danych:

Aplikacja przechowuje dane dotyczące poziomów, wyników graczy oraz szczegółów rozgrywki, w tym:

- **Poziomy:** Informacje o układzie cukierków, wymaganiach poziomu i bonusach.
- **Wyniki graczy:** Przechowywanie wyników poszczególnych graczy.
- **Rozgrywka:** Aktualny stan gry, ruchy gracza, zdobyte punkty.

### Diagramy architektury:

Architektura oparta jest na strukturze MVC (Model-Widok-Kontroler), gdzie:

- **Model:** Odpowiada za logikę gry, zarządzanie poziomami i wynikami.
- **Widok (View):** Prezentuje interfejs użytkownika.
- **Kontroler (Controller):** Zarządza komunikacją między modelem a widokiem.

## Implementacja:

### Opis technologii:

- **Frontend:** HTML, CSS, JavaScript (React.js).
- **Backend:** Node.js z Express.js (obsługa logiki gry i integracji z bazą danych).
- **Baza danych:** MongoDB (przechowywanie danych o poziomach, wynikach i graczach).

### Struktura kodu:

- _Katalogi/pliki:_ Oddzielne pliki dla logiki gry, interfejsu użytkownika, zarządzania danymi.
- _Style pisania kodu:_ Zastosowanie modularności, czytelności i komentarzy w kodzie.

## Testowanie:

### Plan testów:

- **Testy jednostkowe:** Sprawdzenie poprawności logiki gry i zarządzania poziomami.
- **Testy integracyjne:** Upewnienie się, że komponenty współpracują ze sobą poprawnie.
- **Testy interfejsu użytkownika:** Sprawdzenie interakcji z użytkownikiem na różnych urządzeniach.
- **Testy wydajnościowe:** Ocena wydajności gry przy różnych obciążeniach.

### Procedury testowania:

- Opracowanie zestawu przypadków testowych dla każdej funkcji aplikacji.
- Ustalenie procedur raportowania i naprawiania znalezionych błędów.

## Wdrożenie i konserwacja:

### Plan wdrożenia:

- **Etapy wdrażania:** Testowanie, poprawki, publikacja na platformach dostępnych dla użytkowników.
- **Terminy:** Określenie dat planowanych etapów.

### Procedury konserwacji:

- **Wsparcie techniczne:** Ustanowienie kanałów komunikacji z użytkownikami w celu zgłaszania problemów.
- **Aktualizacje:** Planowanie regularnych aktualizacji w zależności od potrzeb i feedbacku użytkowników.

## Harmonogram:

### Plan projektu:

- **Etapy realizacji:** Podział prac na konkretne zadania (np. implementacja logiki gry, interfejsu, testowanie).
- **Terminy:** Określenie czasu potrzebnego na każdy etap.

## Kosztorys:

### Szacunkowe koszty:

- **Rozwój aplikacji:** Wg godzin pracy lub zespołu programistów.
- **Koszty utrzymania:** Serwery, ewentualne opłaty za usługi zewnętrzne, wsparcie techniczne.

---

[English](/README.md)
