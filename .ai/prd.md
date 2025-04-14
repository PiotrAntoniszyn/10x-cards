# Dokument wymagań produktu (PRD) - System Fiszek Edukacyjnych

## 1. Przegląd produktu
System Fiszek Edukacyjnych to aplikacja web, której celem jest ułatwienie nauki poprzez tworzenie oraz zarządzanie fiszkami. Aplikacja umożliwia:
- Ręczne tworzenie fiszek przez użytkownika.
- Automatyczne generowanie fiszek przez AI na podstawie wprowadzonego tekstu.
- Szybką walidację, edycję i usuwanie fiszek.
- Rejestrację i logowanie użytkowników z wykorzystaniem loginu i hasła (przy zachowaniu unikalności loginu).
- Monitorowanie i prezentację statystyk dotyczących generowania oraz walidacji fiszek, co ma wspierać podejmowanie decyzji rozwojowych.

## 2. Problem użytkownika
Ręczne tworzenie wysokiej jakości fiszek edukacyjnych bywa czasochłonne i wymaga znacznego wysiłku. Użytkownicy potrzebują intuicyjnego narzędzia, które:
- Automatycznie generuje fiszki na podstawie wprowadzonego tekstu, zmniejszając nakład pracy.
- Umożliwia łatwą walidację (akceptację, edycję, usunięcie) wygenerowanych fiszek.
- Zapewnia prosty interfejs umożliwiający szybkie tworzenie i zarządzanie fiszkami podczas krótkich sesji nauki.

## 3. Wymagania funkcjonalne
1. Rejestracja i logowanie:
   - Użytkownik może zarejestrować konto, podając unikalny login i hasło.
   - Po rejestracji następuje automatyczne logowanie, bez dodatkowej weryfikacji.
2. Tworzenie fiszek:
   - Tryb manualny: Użytkownik wypełnia formularz, gdzie przód fiszki jest ograniczony do 200 znaków, a tył do 400 znaków.
   - Tryb automatyczny: Użytkownik wprowadza tekst, aplikacja wysyła tekst do modelu LLM za pośrednictwem API, model proponuje zestaw fiszek (pytania i odpowiedzi), a fiszki są przedstawiane użytkownikowi za pomocą listy z możliwością akceptacji, edycji bądź usunięcia.
3. Walidacja treści fiszek:
   - System waliduje, czy przód fiszki nie przekracza 200 znaków oraz tył nie przekracza 400 znaków.
   - W przypadku przekroczenia limitu, użytkownik otrzymuje komunikat o błędzie.
4. Walidacja i zatwierdzanie fiszek wygenerowanych przez AI:
   - Fiszki generowane przez AI są początkowo traktowane jako kandydaci.
   - Użytkownik może zaakceptować, edytować lub usunąć każdą fiszkę przed jej finalnym dodaniem do bazy.
5. Edycja fiszek:
   - Użytkownik może edytować fiszkę bezpośrednio z widoku listy lub podczas walidacji.
   - Zmiany są zapisywane natychmiast po dokonaniu edycji.
6. Usuwanie fiszek:
   - Usunięcie fiszki wymaga potwierdzenia (komunikat „Czy na pewno chcesz usunąć fiszkę?”), aby uniknąć przypadkowych operacji.
7. Statystyki:
   - System gromadzi logi operacji związanych z generowaniem fiszek przez AI.
   - Użytkownik ma dostęp do statystyk (np. procent akceptacji vs. odrzutów) przez opcję „Statystyki” w interfejsie.
8. Przechowywanie i skalowalność:
    - Dane o fiszkach i użytkownikach są przechowywane w sposób zapewniający bezpieczeństwo i skalowalność.
9. Wymagania prawne:
    - Dane osobowe użytkowników i fiszek zgodne z RODO
    - Prawo do wglądu i usunięcia danych (konto wraz z fiszkami) na wniosek użytkownika.

## 4. Granice produktu
- Brak zaawansowanego algorytmu powtórek; system wykorzysta gotowe rozwiązania zamiast implementacji nowego algorytmu podobnego do SuperMemo lub Anki.
- Brak integracji z importem formatów takich jak PDF, DOCX, itp.
- Brak opcji współdzielenia zestawów fiszek między użytkownikami.
- Brak integracji z innymi platformami edukacyjnymi.
- Produkt dedykowany wyłącznie platformie web (aplikacje mobilne nie są przewidziane na początkowym etapie).
- Brak implementacji mechanizmu audytu operacji (np. historia zmian) oraz dodatkowych mechanizmów feedbacku od użytkowników.
- Wybór rozwiązania open-source do generowania fiszek zostanie określony w późniejszym terminie.

## 5. Historyjki użytkowników

US-001: Rejestracja i logowanie  
Tytuł: Użytkownik rejestruje konto i loguje się.  
Opis: Użytkownik może założyć konto, podając unikalny login i hasło. Po rejestracji następuje automatyczne logowanie.  
Kryteria akceptacji:
- System umożliwia rejestrację z unikalnym loginem.
- Użytkownik jest automatycznie logowany po rejestracji.

US-002: Manualne tworzenie fiszek  
Tytuł: Użytkownik tworzy fiszkę ręcznie.  
Opis: Użytkownik wypełnia formularz tworzenia fiszki, w którym przód fiszki ma maksymalnie 200 znaków, a tył 400 znaków.  
Kryteria akceptacji:
- Formularz umożliwia wprowadzenie obu pól z odpowiednimi ograniczeniami znaków.
- Fiszka zostaje zapisana po zatwierdzeniu formularza.

US-003: Automatyczne generowanie fiszek przez AI  
Tytuł: Generowanie fiszek przez AI.  
Opis: Użytkownik wprowadza tekst, na podstawie którego AI generuje propozycje fiszek, traktowanych jako kandydaci.  
Kryteria akceptacji:
- AI generuje fiszki na podstawie przekazanego tekstu.
- Wygenerowane fiszki pojawiają się jako kandydaci do walidacji.

US-004: Walidacja fiszek generowanych przez AI  
Tytuł: Walidacja wygenerowanych fiszek przez AI.  
Opis: Użytkownik przegląda listę fiszek wygenerowanych przez AI i ma możliwość akceptacji, edycji lub usunięcia każdej z nich przed finalnym dodaniem do bazy.  
Kryteria akceptacji:
- Użytkownik widzi listę kandydatów fiszek.
- Użytkownik może edytować treść fiszki bezpośrednio w widoku.
- Po akceptacji fiszka trafia do bazy danych.

US-005: Szybka edycja fiszek  
Tytuł: Edycja istniejącej fiszki.  
Opis: Użytkownik może dokonać edycji treści fiszki zarówno z poziomu widoku listy, jak i podczas walidacji fiszek generowanych przez AI.  
Kryteria akceptacji:
- Użytkownik może edytować fiszkę.
- Zmiany są zapisywane natychmiast.
- System sprawdza, czy nowe treści nie przekraczają limitów znaków.

US-006: Usuwanie fiszek z potwierdzeniem  
Tytuł: Usuwanie fiszki.  
Opis: Użytkownik inicjuje usunięcie fiszki, a system wyświetla potwierdzenie („Czy na pewno chcesz usunąć fiszkę?”) przed wykonaniem operacji.  
Kryteria akceptacji:
- Po wybraniu opcji usunięcia, system wyświetla komunikat potwierdzający operację.
- Fiszka zostaje usunięta tylko po potwierdzeniu przez użytkownika.

US-007: Wyświetlanie listy fiszek  
Tytuł: Przeglądanie listy fiszek.  
Opis: Użytkownik widzi pełną listę utworzonych fiszek, obejmującą zarówno fiszki stworzone manualnie, jak i te zatwierdzone po walidacji AI.  
Kryteria akceptacji:
- Lista fiszek jest zawsze aktualna.
- Użytkownik ma możliwość przechodzenia do opcji edycji lub usunięcia każdej fiszki z listy.

US-008: Dostęp do statystyk  
Tytuł: Przeglądanie statystyk generowania fiszek przez AI.  
Opis: Użytkownik wybiera opcję „Statystyki”, aby zobaczyć dane dotyczące akceptacji, odrzutów oraz ewentualnych edycji fiszek generowanych przez AI.  
Kryteria akceptacji:
- Statystyki są wyświetlane w czytelnym formacie.
- Dane obejmują procent akceptowanych i odrzuconych fiszek oraz liczbę edycji.
- Informacje pochodzą z bazy logów operacyjnych.

US-009: Walidacja treści fiszek  
Tytuł: System waliduje długość treści fiszki.  
Opis: Podczas tworzenia lub edycji fiszki, system sprawdza, czy przód nie przekracza 200 znaków, a tył 400 znaków, informując użytkownika o błędzie w przypadku przekroczenia limitu.  
Kryteria akceptacji:
- System mierzy liczbę znaków w czasie rzeczywistym.
- Użytkownik otrzymuje komunikat o błędzie przy przekroczeniu limitu.
- Fiszka nie może być zatwierdzona, jeśli limit znaków został przekroczony.

## 6. Metryki sukcesu
- 75% fiszek generowanych przez AI zostaje zaakceptowanych przez użytkowników.
- 75% wszystkich utworzonych fiszek pochodzi z opcji generowania przez AI.
- Wzrost liczby aktywnych użytkowników oraz ich częstotliwość korzystania z aplikacji.
- Szybkość i intuicyjność interfejsu mierzona poprzez testy użyteczności.
- Dokładność walidacji treści fiszek (utrzymanie limitów 200/400 znaków) oraz reakcje użytkowników.