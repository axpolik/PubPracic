**Witaj! - Twój Pierwszy Projekt: Inteligentny Asystent Inwestora ETF (Wersja z Wyzwaniem!)**

Cześć!

Zanim oficjalnie rozpoczniesz praktyki, chcemy dać Ci szansę na rozgrzewkę i zdobycie pierwszych praktycznych umiejętności w obszarze, który jest dla nas ważny – automatyzacji i analizy danych, z wykorzystaniem narzędzi często używanych w połączeniu z chmurą Microsoft Azure.

Twoim zadaniem będzie stworzenie prostego "agenta AI" (a dokładniej: zautomatyzowanego skryptu), który będzie codziennie analizował rynek wybranych funduszy ETF i wysyłał e-mailem podsumowanie wraz z podstawowymi sugestiami. Tym razem jednak, zamiast gotowego kodu, dostaniesz wskazówki i fragmenty, a resztę logiki będziesz musiał(a) zbudować samodzielnie!

**Cel projektu:**

1.  **Nauka samodzielnego programowania:** Zrozumiesz, jak przełożyć wymagania na działający kod w Pythonie.
2.  **Praca z danymi i API:** Nauczysz się, jak samodzielnie znaleźć sposób na pobranie i przetworzenie danych z zewnętrznego źródła.
3.  **Rozwiązywanie problemów:** Zmierzysz się z typowymi wyzwaniami programistycznymi: obsługą błędów, przetwarzaniem różnych formatów danych.
4.  **Automatyzacja zadań:** Zbudujesz program wykonujący powtarzalne czynności.
5.  **Podstawy finansów i AI:** Zrozumiesz podstawy ETF i jak proste reguły mogą naśladować podejmowanie decyzji.

**Co zbudujesz?**

Program ("Agent ETF"), który każdego dnia:

1.  **Samodzielnie pobierze** aktualne dane (cenę zamknięcia) dla jednego lub kilku wybranych funduszy ETF z publicznie dostępnego API.
2.  **Obliczy** zmianę procentową ceny w stosunku do poprzedniego dnia.
3.  **Na podstawie zdefiniowanych przez Ciebie reguł** wygeneruje prostą rekomendację (np. KUP, SPRZEDAJ, TRZYMAJ).
4.  **Sformatuje** podsumowanie (np. "ETF XYZ: Zmiana dzienna +0.8%, Cena: 150 USD, Sugestia: TRZYMAJ").
5.  **Wyśle** podsumowanie na Twój adres e-mail.

**Dlaczego ten projekt?**

To wyzwanie pozwoli Ci naprawdę wgryźć się w proces tworzenia oprogramowania. Umiejętności, które zdobędziesz – samodzielne szukanie rozwiązań, debugowanie kodu, praca z Pythonem i API – są kluczowe w naszej branży i świetnie przygotują Cię do pracy z technologiami chmurowymi jak Microsoft Azure.

**Krok 1: Zdobądź wiedzę teoretyczną (Fundamenty)**

1.  **Podstawy Programowania w Pythonie:**
    *   **Dlaczego Python?** Jest stosunkowo łatwy do nauki, ma mnóstwo gotowych narzędzi (bibliotek) i jest szeroko używany w analizie danych, AI i web development'cie (również w Azure!).
    *   **Gdzie się uczyć?**
        *   **Oficjalny tutorial Python (PL):** [https://docs.python.org/pl/3/tutorial/index.html](https://docs.python.org/pl/3/tutorial/index.html) (Zacznij od rozdziałów 1-5).
        *   **Codecademy (częściowo darmowy kurs interaktywny):** [https://www.codecademy.com/learn/learn-python-3](https://www.codecademy.com/learn/learn-python-3)
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

**Krok 2: Przygotuj narzędzia**

1.  **Python:** Pobierz i zainstaluj najnowszą wersję Pythona 3 ze strony: [https://www.python.org/downloads/](https://www.python.org/downloads/) (Upewnij się, że podczas instalacji zaznaczyłeś opcję "Add Python to PATH").
2.  **Edytor Kodu (IDE):** Polecamy Visual Studio Code (VS Code). Jest darmowy, potężny i popularny. Pobierz go stąd: [https://code.visualstudio.com/](https://code.visualstudio.com/). Po instalacji zainstaluj rozszerzenie "Python" od Microsoftu (w zakładce Extensions w VS Code).
3.  **Konto E-mail:** Będziesz potrzebować adresu e-mail do wysyłania podsumowań (może być Twój prywatny Gmail, ale o tym później).
4.  **Klucz API do danych finansowych:** Potrzebujesz źródła danych o ETF. Dobrym i darmowym (z limitami) miejscem na start jest Alpha Vantage:
    *   Wejdź na [https://www.alphavantage.co/support/#api-key](https://www.alphavantage.co/support/#api-key)
    *   Wypełnij krótki formularz, aby otrzymać darmowy klucz API (API Key). Zapisz go sobie, będzie potrzebny w kodzie.

**Krok 3: Budowa Agenta ETF - Wskazówki i Fragmenty Kodu**

Otwórz VS Code, stwórz nowy plik (np. `agent_etf.py`). Zaczynamy budowę, ale tym razem Ty wypełniasz luki!

1.  **Import potrzebnych bibliotek:**
    *   Będziesz potrzebować bibliotek do wysyłania zapytań HTTP, pracy z JSON, wysyłania e-maili i obsługi daty/czasu. Jakich? Poszukaj w dokumentacji Pythona lub zasobach z Kroku 1.
    *   **Wskazówka:** Popularna biblioteka do zapytań HTTP to `requests`. Do e-maili często używa się `smtplib` i `email.mime.text`. Upewnij się, że je zainstalowałeś (`pip install ...`).

2.  **Konfiguracja:**
    *   Zdefiniuj zmienne na początku skryptu, aby przechowywać Twój klucz API, symbol ETF, dane do logowania e-mail. To dobra praktyka.
        ```python
        # === Konfiguracja ===
        API_KEY = "TWOJ_KLUCZ_API_Z_ALPHA_VANTAGE"
        ETF_SYMBOL = "SPY" # Możesz zmienić na inny
        EMAIL_SENDER = "twoj_email@gmail.com"
        EMAIL_PASSWORD = "twoje_haslo_aplikacji_gmail" # Pamiętaj o haśle aplikacji!
        EMAIL_RECEIVER = "odbiorca@example.com"
        # === Koniec Konfiguracji ===
        ```

3.  **Pobieranie danych z API (Twoje Zadanie!):**
    *   Musisz skonstruować URL do API Alpha Vantage (funkcja `TIME_SERIES_DAILY`). Dokumentację znajdziesz na ich stronie.
    *   Użyj biblioteki `requests`, aby wysłać zapytanie GET pod ten URL.
    *   Sprawdź, czy odpowiedź serwera jest poprawna (kod statusu 200).
    *   Przekonwertuj odpowiedź (która będzie w formacie JSON) na słownik Pythona.
    *   **Fragment-Wskazówka:**
        ```python
        import requests # Upewnij się, że masz ten import

        def get_etf_data(api_key, symbol):
            # Zbuduj URL używając f-string lub innego formatowania
            # Dokumentacja Alpha Vantage podpowie, jakich parametrów użyć
            url = f'https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol={symbol}&apikey={api_key}&outputsize=compact' # To jest przykład, dostosuj go!

            print(f"Wysyłam zapytanie do: {url}") # Dobrze jest wiedzieć, co się dzieje
            try:
                response = requests.get(url)
                response.raise_for_status() # To zgłosi błąd dla statusów 4xx/5xx
                # Co dalej? Jak przetworzyć 'response', aby dostać dane?
                # Użyj metody .json() na obiekcie response
                data = response.json()

                # WAŻNE: Sprawdź, czy 'data' zawiera oczekiwane klucze!
                # Np. czy istnieje klucz 'Time Series (Daily)'?
                # Jeśli nie, API mogło zwrócić błąd (np. zły symbol, limit zapytań) - obsłuż to!
                if "Time Series (Daily)" not in data:
                   print("Błąd w odpowiedzi API:", data)
                   return None # Zwróć None lub rzuć wyjątek, jeśli coś poszło nie tak

                return data['Time Series (Daily)'] # Zwróć tylko część z danymi dziennymi

            except requests.exceptions.RequestException as e:
                print(f"Błąd połączenia z API: {e}")
                return None
            # Jakie inne błędy mogą tu wystąpić? Pomyśl o `json.JSONDecodeError`.
            except Exception as e: # Ogólny handler na inne niespodziewane błędy
                 print(f"Wystąpił niespodziewany błąd podczas pobierania danych: {e}")
                 return None

        # Wywołaj funkcję i zobacz, co zwraca
        daily_data = get_etf_data(API_KEY, ETF_SYMBOL)
        # print(daily_data) # Odkomentuj, żeby zobaczyć strukturę danych
        ```
    *   **Twoje zadanie:** Dokończ funkcję `get_etf_data`, dodaj obsługę błędów (co jeśli API zwróci błąd w JSONie? Co jeśli nie ma klucza 'Time Series (Daily)'?), przetestuj ją.

4.  **Przetwarzanie danych (Twoje Zadanie!):**
    *   Mając `daily_data` (który jest słownikiem, gdzie klucze to daty), musisz:
        *   Znaleźć najnowszą datę i datę poprzednią. (Wskazówka: klucze słownika, sortowanie).
        *   Wyciągnąć cenę zamknięcia ('4. close') dla obu tych dat. Pamiętaj, że te wartości są tekstowe - przekonwertuj je na liczby (`float`).
        *   Obliczyć zmianę procentową: `((nowa_cena - stara_cena) / stara_cena) * 100`.
    *   **Wskazówka:** Ostrożnie z dostępem do słowników. Co jeśli danych jest mniej niż 2 dni? Użyj `try...except KeyError` lub sprawdzaj długość listy dat.

5.  **Generowanie Rekomendacji (Twoje Zadanie!):**
    *   Napisz serię instrukcji `if/elif/else`, które na podstawie obliczonej zmiany procentowej (`price_change_percent`) przypiszą odpowiedni tekst rekomendacji do zmiennej (np. `recommendation`).
    *   **Fragment-Wskazówka:**
        ```python
        recommendation = "Brak wystarczających danych" # Domyślna wartość

        # Upewnij się, że masz obliczoną zmianę procentową (price_change_percent)
        # Pamiętaj, że mogła nie zostać obliczona, jeśli było za mało danych
        # if price_change_percent is not None: # Dobry pomysł, żeby to sprawdzić!

        # Zdefiniuj WŁASNE proste reguły, np.:
        # if price_change_percent > 2.0:
        #     recommendation = "ROZWAŻ SPRZEDAŻ (Silny wzrost)"
        # elif ... : # Dodaj więcej warunków
        #     recommendation = "..."
        # else:
        #     recommendation = "TRZYMAJ (Stabilnie)"

        print(f"Rekomendacja: {recommendation}")
        ```
    *   **Twoje zadanie:** Zdefiniuj progi procentowe i odpowiadające im komunikaty. Bądź kreatywny(a), ale pamiętaj, że to tylko symulacja!

6.  **Formatowanie Podsumowania do E-maila (Twoje Zadanie!):**
    *   Stwórz zmienną tekstową (`subject`) na temat e-maila.
    *   Stwórz drugą zmienną tekstową (`body`) zawierającą treść wiadomości. Użyj f-stringów lub metody `.format()`, aby wstawić do treści aktualne dane (symbol ETF, datę, cenę, zmianę procentową, rekomendację).
    *   **Wskazówka:** Użyj potrójnych cudzysłowów (`"""Tekst..."""`) do stworzenia wieloliniowego tekstu treści e-maila. Pamiętaj o dodaniu informacji, że to automatyczna wiadomość edukacyjna i nie jest poradą inwestycyjną.

7.  **Wysyłanie E-maila (Twoje Zadanie!):**
    *   Użyj biblioteki `smtplib` do wysłania e-maila. Będziesz musiał(a):
        *   Połączyć się z serwerem SMTP (dla Gmaila: `smtp.gmail.com`, port 465 z SSL).
        *   Zalogować się używając swojego adresu e-mail i **hasła do aplikacji**.
        *   Stworzyć obiekt wiadomości (np. używając `email.mime.text.MIMEText`), ustawiając nadawcę, odbiorcę, temat i treść. Pamiętaj o kodowaniu UTF-8 dla polskich znaków!
        *   Wysłać wiadomość.
        *   Zamknąć połączenie z serwerem.
    *   **Fragment-Wskazówka:**
        ```python
        import smtplib
        from email.mime.text import MIMEText # Upewnij się, że masz ten import

        def send_email(sender, password, receiver, subject, body):
            # Stwórz obiekt wiadomości MIMEText
            # Ustaw kodowanie 'utf-8'
            # message = MIMEText(body, 'plain', 'utf-8')
            # message['Subject'] = ...
            # message['From'] = ...
            # message['To'] = ...

            try:
                # Połącz się z serwerem SMTP (przykład dla Gmaila)
                # server = smtplib.SMTP_SSL('smtp.gmail.com', 465)
                # server.ehlo() # Przywitaj się z serwerem
                # server.login(sender, password)
                # server.sendmail(sender, receiver, message.as_string()) # Wyślij!
                # server.close()
                print(f"\nE-mail (symulacja wysyłki) do {receiver} wysłany.") # Na razie symulacja
            except Exception as e:
                print(f"\nNie udało się wysłać e-maila: {e}")
                # Tutaj dodaj faktyczny kod wysyłki w bloku try
                pass # Usuń 'pass' gdy dodasz prawdziwy kod

        # Wywołaj funkcję pod koniec skryptu
        # Pamiętaj, aby przekazać poprawnie temat (subject) i treść (body)
        # send_email(EMAIL_SENDER, EMAIL_PASSWORD, EMAIL_RECEIVER, subject, body)
        ```
    *   **Twoje zadanie:** Uzupełnij funkcję `send_email`, aby faktycznie wysyłała e-mail. Obsłuż możliwe błędy (np. błąd logowania).

8.  **Testowanie i Debugowanie:**
    *   Uruchamiaj skrypt (`python agent_etf.py`) często, po każdej większej zmianie.
    *   Używaj `print()` do wyświetlania wartości zmiennych w różnych miejscach kodu, aby sprawdzić, czy są poprawne.
    *   Czytaj uważnie komunikaty błędów – one często podpowiadają, co poszło nie tak.
    *   Testuj różne scenariusze: co jeśli API nie odpowie? Co jeśli nie ma danych historycznych?

**Krok 4: Co dalej? (Opcjonalne pomysły na rozwój)**

*   Analiza wielu ETF-ów.
*   Bardziej złożone reguły (np. średnia krocząca).
*   Zapisywanie historii do pliku.
*   Automatyczne uruchamianie (Harmonogram Zadań / cron).
*   Wizualizacja danych (`matplotlib`).

**Masz pytania? Utknąłeś/Utknęłaś?**

To część procesu! Zapisuj problemy, na które natrafiasz. Spróbuj poszukać rozwiązań w dokumentacji Pythona, na stronach typu Stack Overflow (wpisując komunikat błędu lub opis problemu po angielsku). Kiedy zaczniesz praktyki, przejrzymy Twój kod i omówimy wyzwania. Nie poddawaj się!

Powodzenia w budowaniu Twojego pierwszego agenta!

Zespół XPLUS
