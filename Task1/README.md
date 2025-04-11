# Projekt 1: Agent Analizy Rynku ETF

Twoim celem jest zbudowanie prostego, zautomatyzowanego skryptu w Pythonie (nazwijmy go "Agent ETF"), który codziennie pobierze dane o wybranym funduszu ETF, przeanalizuje je i wyśle podsumowanie e-mailem.

To zadanie pozwoli Ci przećwiczyć podstawy Pythona, pracę z zewnętrznymi serwisami (API), przetwarzanie danych i automatyzację – umiejętności kluczowe w naszej pracy, często wykorzystywane w połączeniu z chmurą Microsoft Azure. Dodatkowo, będziesz używać systemu kontroli wersji Git do zapisywania postępów swojej pracy.

## Co Zbudujesz?

Program ("Agent ETF"), który każdego dnia:

1.  **Samodzielnie pobierze** aktualne dane (cenę zamknięcia) dla jednego wybranego funduszu ETF z publicznie dostępnego API (np. Alpha Vantage).
2.  **Obliczy** zmianę procentową ceny w stosunku do poprzedniego dnia.
3.  **Na podstawie zdefiniowanych przez Ciebie reguł** wygeneruje prostą rekomendację (np. KUP, SPRZEDAJ, TRZYMAJ).
4.  **Sformatuje** podsumowanie tekstowe zawierające kluczowe informacje.
5.  **Wyśle** to podsumowanie na Twój adres e-mail.

## Dlaczego Ten Projekt?

*   **Praktyczne programowanie:** Zastosujesz teorię Pythona w realnym zadaniu.
*   **Praca z API:** Nauczysz się komunikować z zewnętrznymi usługami.
*   **Podstawy analizy:** Zobaczysz, jak kod może pomagać w interpretacji danych.
*   **Automatyzacja:** Zrozumiesz, jak oszczędzać czas, automatyzując zadania.
*   **Kontrola Wersji (Git):** Nauczysz się podstawowych komend Git do śledzenia zmian w kodzie – to fundamentalna umiejętność każdego programisty.

## Krok 1: Wiedza Teoretyczna (Fundamenty)

Zanim zaczniesz kodować, poświęć trochę czasu na zrozumienie podstaw. Oto zasoby, które Ci pomogą:

1.  **Podstawy Programowania w Pythonie:**
    *   **Dlaczego Python?** Jest stosunkowo łatwy do nauki, ma mnóstwo gotowych narzędzi (bibliotek) i jest szeroko używany w analizie danych, AI i web development'cie (również w Azure!).
    *   **Gdzie się uczyć?**
        *   **Oficjalny tutorial Python (PL):** [https://docs.python.org/pl/3/tutorial/index.html](https://docs.python.org/pl/3/tutorial/index.html) (Zacznij od rozdziałów 1-5).
        *   **Kanał YouTube "Kurs Python od podstaw dla zielonych" M. Mikulskiego:** [https://www.youtube.com/playlist?list=PL6aekdNhY7DBGiMXNMRIrM9Qfg0sjsdvU](https://www.youtube.com/playlist?list=PL6aekdNhY7DBGiMXNMRIrM9Qfg0sjsdvU)
    *   **Kluczowe koncepty do zrozumienia:** Zmienne, typy danych (liczby, napisy, listy, słowniki), instrukcje warunkowe (`if`, `elif`, `else`), pętle (`for`, `while`), funkcje, importowanie modułów/bibliotek.

2.  **Co to jest API?**
    *   **Wyjaśnienie:** Pomyśl o API jak o kelnerze w restauracji. Ty (Twój program) mówisz kelnerowi (API), co chcesz z kuchni (serwera z danymi), a on Ci to przynosi w określony sposób. Będziesz używać API do pobierania danych o ETF-ach.
    *   **Gdzie się uczyć?**
        *   **Krótki film wyjaśniający (EN):** Wyszukaj na YouTube "What is an API?". Jest wiele dobrych, krótkich animacji.
        *   **Artykuł (EN):** [https://www.freecodecamp.org/news/what-is-an-api-in-english-please-b880a3214a82/](https://www.freecodecamp.org/news/what-is-an-api-in-english-please-b880a3214a82/)
    *   **Kluczowe koncepty:** Jak działa zapytanie HTTP (GET), co to jest JSON (format danych, który często zwraca API).

3.  **Co to są Fundusze ETF?**
    *   **Wyjaśnienie:** To rodzaj funduszu inwestycyjnego notowanego na giełdzie, jak akcje. Często śledzą one jakiś indeks (np. WIG20, S&P 500) lub sektor (np. technologia, energia).
    *   **Gdzie się uczyć?**
        *   **Artykuł na Analizy.pl:** [https://www.analizy.pl/fundusze-etf/slownik/1305/etf-(exchange-traded-fund).html](https://www.analizy.pl/fundusze-etf/slownik/1305/etf-(exchange-traded-fund).html)
        *   **Strona Beta Securities (polski dostawca ETF):** [https://betasecurities.pl/co-to-jest-etf](https://betasecurities.pl/co-to-jest-etf)
    *   **Kluczowe koncepty:** Czym jest ETF, jak jest wyceniany (cena na giełdzie), przykład popularnego ETF (np. śledzący S&P 500 - symbol SPY, lub polski - np. na WIG20). W tym projekcie skupimy się głównie na **dziennej cenie zamknięcia**.

4.  **Podstawy Git:** Co to jest repozytorium, commit, add, status, log.
    *   *Zasoby:* [Oficjalna książka Pro Git (PL - rozdziały 1-2)](https://git-scm.com/book/pl/v2), [Interaktywny tutorial Git](https://try.github.io/).

## Krok 2: Przygotowanie Narzędzi

Potrzebujesz (zakładamy, że masz je już zainstalowane zgodnie z głównym README):

1.  **Python 3**
2.  **Visual Studio Code (VS Code)** z rozszerzeniem Python
3.  **Git**
4.  **Konto E-mail** (np. Gmail z wygenerowanym **hasłem do aplikacji**)
5.  **Klucz API** z Alpha Vantage ([https://www.alphavantage.co/support/#api-key](https://www.alphavantage.co/support/#api-key))

## Krok 3: Budowa Agenta ETF (Wskazówki i Fragmenty Kodu)

Otwórz folder tego projektu (`Projekt_01_Agent_ETF`) w VS Code. Główny kod będziesz pisać w pliku `agent_etf.py` (możesz go stworzyć, jeśli jeszcze nie istnieje).

### Praca z Git podczas Projektu

Zanim zaczniesz kodować, poznaj podstawowy cykl pracy z Gitem, którego będziesz używać:

1.  **Sprawdź status:** Zobacz, które pliki zostały zmienione.
    ```bash
    git status
    ```
2.  **Dodaj zmiany do "poczekalni" (staging area):** Wybierz pliki, które chcesz zapisać w następnym "punkcie kontrolnym" (commicie). Najczęściej będziesz dodawać plik, nad którym pracujesz.
    ```bash
    git add agent_etf.py
    ```
    (lub `git add .` aby dodać wszystkie zmienione pliki w bieżącym folderze i podfolderach)
3.  **Zapisz punkt kontrolny (commit):** Stwórz "migawkę" swojego kodu z krótkim opisem wprowadzonych zmian.
    ```bash
    git commit -m "Opis twojej zmiany, np. Dodano funkcję pobierania danych ETF"
    ```
4.  **(Opcjonalnie) Zobacz historię:** Wyświetl listę zapisanych commitów.
    ```bash
    git log --oneline
    ```

**Staraj się robić commity często!** Po każdym zrealizowanym, logicznym etapie (np. "dodałem funkcję X", "poprawiłem błąd Y", "dodałem obsługę Z"), zrób `git add` i `git commit`. To pomoże Ci śledzić postępy i ewentualnie wrócić do poprzedniej działającej wersji.

---

### Zaczynamy Kodowanie!

1.  **Import potrzebnych bibliotek:**
    *   Zaimportuj biblioteki do: zapytań HTTP (`requests`), obsługi JSON (`json`), wysyłki e-maili (`smtplib`, `email.mime.text`), pracy z datami (`datetime`).
    *   Pamiętaj o instalacji, jeśli ich nie masz (`pip install requests`).

2.  **Konfiguracja:**
    *   Zdefiniuj stałe na początku skryptu dla klucza API, symbolu ETF, danych do e-maila.
        ```python
        # === Konfiguracja ===
        API_KEY = "TWOJ_KLUCZ_API_Z_ALPHA_VANTAGE"
        ETF_SYMBOL = "SPY" # Przykładowy symbol, możesz zmienić
        EMAIL_SENDER = "twoj_email@gmail.com"
        EMAIL_PASSWORD = "twoje_haslo_aplikacji_gmail" # Hasło aplikacji!
        EMAIL_RECEIVER = "odbiorca@example.com"
        # === Koniec Konfiguracji ===
        ```
    *   **Zapisz postęp:**
        ```bash
        git add agent_etf.py
        git commit -m "Initial setup and configuration variables"
        ```

3.  **Pobieranie danych z API (Twoje Zadanie!):**
    *   Napisz funkcję `get_etf_data(api_key, symbol)`, która:
        *   Skonstruuje poprawny URL do API Alpha Vantage (`TIME_SERIES_DAILY`).
        *   Użyje `requests.get()` do pobrania danych.
        *   Sprawdzi status odpowiedzi (`response.raise_for_status()`).
        *   Przetworzy odpowiedź JSON na słownik Pythona (`response.json()`).
        *   **Ważne:** Sprawdzi, czy odpowiedź zawiera oczekiwany klucz (`'Time Series (Daily)'`). Jeśli nie, powinna zwrócić `None` lub zgłosić błąd i obsłużyć go (np. wydrukować komunikat). Pamiętaj też o obsłudze błędów połączenia (`requests.exceptions.RequestException`) i błędów dekodowania JSON (`json.JSONDecodeError`).
    *   **Fragment-Wskazówka:**
        ```python
        import requests
        import json # Upewnij się, że masz te importy

        def get_etf_data(api_key, symbol):
            url = f'https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol={symbol}&apikey={api_key}&outputsize=compact'
            print(f"Pobieram dane dla {symbol}...")
            try:
                response = requests.get(url)
                response.raise_for_status()
                data = response.json()
                if "Time Series (Daily)" not in data:
                   print(f"Błąd w odpowiedzi API dla {symbol}:", data)
                   return None
                return data['Time Series (Daily)']
            except requests.exceptions.RequestException as e:
                print(f"Błąd połączenia z API: {e}")
                return None
            except json.JSONDecodeError:
                print(f"Błąd przetwarzania odpowiedzi JSON z API dla {symbol}. Odpowiedź: {response.text}")
                return None
            except Exception as e:
                 print(f"Wystąpił niespodziewany błąd podczas pobierania danych: {e}")
                 return None

        # Przetestuj funkcję
        daily_data = get_etf_data(API_KEY, ETF_SYMBOL)
        # if daily_data:
        #    print("Pobrano dane!")
        # else:
        #    print("Nie udało się pobrać danych.")
        ```
    *   **Zapisz postęp:** Po napisaniu i przetestowaniu funkcji:
        ```bash
        git add agent_etf.py
        git commit -m "Implemented function to fetch ETF data from Alpha Vantage with error handling"
        ```

4.  **Przetwarzanie danych (Twoje Zadanie!):**
    *   Jeśli `get_etf_data` zwróciło dane (`daily_data` nie jest `None`):
        *   Pobierz klucze słownika `daily_data` (daty) i posortuj je malejąco, aby uzyskać najnowsze daty na początku.
        *   Sprawdź, czy masz dane z co najmniej dwóch dni.
        *   Wyciągnij cenę zamknięcia (`'4. close'`) dla najnowszej i poprzedniej daty. Pamiętaj o konwersji na `float()`.
        *   Oblicz zmianę procentową.
        *   Obsłuż przypadek, gdy jest za mało danych do obliczenia zmiany.
    *   **Wskazówka:** Użyj bloku `if daily_data:` aby kontynuować tylko jeśli dane zostały poprawnie pobrane.

5.  **Generowanie Rekomendacji (Twoje Zadanie!):**
    *   Napisz logikę (`if/elif/else`), która na podstawie `price_change_percent` wygeneruje tekstową rekomendację. Zdefiniuj własne progi (np. > 1.5% "Rozważ Zmniejszenie", < -1.5% "Rozważ Zakup" itp.).
    *   Przypisz rekomendację do zmiennej `recommendation`. Obsłuż przypadek, gdy zmiana procentowa nie mogła być obliczona.
    *   **Zapisz postęp:** Po zaimplementowaniu przetwarzania danych i logiki rekomendacji:
        ```bash
        git add agent_etf.py
        git commit -m "Added logic for data processing and generating basic recommendations"
        ```

6.  **Formatowanie Podsumowania do E-maila (Twoje Zadanie!):**
    *   Stwórz zmienne `subject` (temat) i `body` (treść) e-maila.
    *   Użyj f-stringów, aby wstawić do treści e-maila: symbol ETF, datę, cenę, zmianę procentową (jeśli dostępna) i wygenerowaną rekomendację.
    *   Dodaj standardową stopkę informującą, że to **wiadomość automatyczna i nie jest poradą inwestycyjną**.

7.  **Wysyłanie E-maila (Twoje Zadanie!):**
    *   Napisz funkcję `send_email(sender, password, receiver, subject, body)`, która:
        *   Użyje `smtplib` do połączenia z serwerem SMTP (np. Gmaila: `smtp.gmail.com`, port 465, SSL).
        *   Zaloguje się (`server.login()`) używając `EMAIL_SENDER` i `EMAIL_PASSWORD` (hasło aplikacji!).
        *   Stworzy obiekt wiadomości `MIMEText` z treścią `body`, ustawiając kodowanie `utf-8`. Ustaw też nagłówki 'Subject', 'From', 'To'.
        *   Wyśle e-mail (`server.sendmail()`).
        *   Zamknie połączenie (`server.close()`).
        *   Obsłuży potencjalne błędy w bloku `try...except`.
    *   Wywołaj tę funkcję na końcu skryptu, jeśli wszystkie poprzednie kroki się powiodły.
    *   **Zapisz postęp:**
        ```bash
        git add agent_etf.py
        git commit -m "Implemented email sending functionality with error handling"
        ```

8.  **Testowanie i Debugowanie:**
    *   Uruchamiaj skrypt (`python agent_etf.py`) często.
    *   Używaj `print()` do sprawdzania wartości zmiennych.
    *   Czytaj komunikaty błędów!
    *   Sprawdzaj, czy e-maile dochodzą i czy ich treść jest poprawna.

**Krok 4: Co dalej? (Opcjonalne pomysły na rozwój)**

Jeśli poradzisz sobie z podstawową wersją, oto kilka pomysłów, jak możesz rozwinąć projekt (ale nie jest to wymagane!):

*   **Analiza większej liczby ETF-ów:** Zmodyfikuj kod, aby analizował listę kilku różnych ETF-ów.
*   **Bardziej złożone reguły:** Dodaj obliczanie prostej średniej kroczącej (np. z 5 dni) i użyj jej w regułach rekomendacji.
*   **Zapisywanie historii:** Zapisuj codzienne dane i rekomendacje do pliku (np. CSV lub JSON), aby móc śledzić historię.
*   **Automatyczne uruchamianie:** Dowiedz się, jak można ustawić automatyczne uruchamianie skryptu codziennie o określonej porze (np. za pomocą Harmonogramu Zadań w Windows lub `cron` w systemach Linux/MacOS). W przyszłości na praktykach pokażemy Ci, jak takie rzeczy robić w chmurze Azure (np. Azure Functions, Logic Apps).
*   **Wizualizacja:** Spróbuj użyć biblioteki `matplotlib`, aby narysować prosty wykres ceny ETF.

**Ważna Uwaga Końcowa (Disclaimer)**

Pamiętaj, że ten projekt ma charakter **wyłącznie edukacyjny**. Stworzony agent i jego rekomendacje są oparte na bardzo uproszczonych zasadach. **Nigdy nie używaj tego typu automatycznych sugestii do podejmowania prawdziwych decyzji inwestycyjnych bez dogłębnej analizy i zrozumienia ryzyka.** Rynek finansowy jest złożony, a inwestowanie wiąże się z ryzykiem utraty kapitału.

**Masz pytania?**

To naturalne, że podczas pracy nad projektem pojawią się pytania lub trudności. Spisuj je sobie. Spróbuj poszukać rozwiązań w dokumentacji Pythona, na stronach typu Stack Overflow (wpisując komunikat błędu lub opis problemu po angielsku). Okresowo wysylaj do nas, chętnie na nie odpowiemy i pomożemy Ci rozwiązać problemy. Nie bój się pytać – to najlepszy sposób na naukę!

Powodzenia! Jesteśmy ciekawi efektów Twojej pracy!
