# **Projekt 2: Agregator Nastrojów Rynkowych**

Bazując na umiejętnościach zdobytych w Projekcie 1, Twoim kolejnym celem jest zbudowanie bardziej zaawansowanego narzędzia w Pythonie – "Agregatora Nastrojów Rynkowych". Skrypt ten będzie zbierał nagłówki wiadomości dotyczące wybranych aktywów (np. akcji, ETFów) z różnych źródeł (API), przeprowadzał podstawową analizę sentymentu tych nagłówków, zapisywał wyniki i prezentował zagregowane podsumowanie.

To zadanie pozwoli Ci pogłębić wiedzę z zakresu pracy z wieloma API, przetwarzania danych tekstowych (podstawy NLP), zarządzania danymi (zapis/odczyt) oraz potencjalnie tworzenia prostych interfejsów użytkownika lub wizualizacji. Są to umiejętności często wykorzystywane przy budowie bardziej złożonych systemów analitycznych, również w środowisku chmury Microsoft Azure.

## **Co Zbudujesz?**

Program ("Agregator Nastrojów"), który:

1. **Pobierze nagłówki wiadomości** dotyczące jednego lub kilku zdefiniowanych symboli (np. 'AAPL', 'TSLA', 'SPY') z co najmniej **dwóch różnych źródeł** (publicznie dostępnych API informacyjnych, np. NewsAPI, Alpha Vantage News & Sentiment).  
2. **Przeprowadzi podstawową analizę sentymentu** dla każdego nagłówka, klasyfikując go jako pozytywny, negatywny lub neutralny (np. na podstawie słów kluczowych lub prostej biblioteki NLP).  
3. **Obliczy zagregowany wskaźnik sentymentu** dla każdego symbolu na podstawie analizy zebranych nagłówków (np. procent nagłówków pozytywnych/negatywnych).  
4. **Zapisze wyniki analizy** (np. symbol, data, nagłówek, sentyment) do pliku w ustrukturyzowanym formacie (np. CSV lub JSON) w celu śledzenia historii.  
5. **Wygeneruje i wyświetli (lub zapisze do pliku) podsumowanie** zawierające zagregowany wskaźnik sentymentu dla każdego analizowanego symbolu.

## **Dlaczego Ten Projekt?**

* **Integracja Wielu API:** Nauczysz się efektywnie komunikować z różnymi zewnętrznymi usługami i agregować z nich dane.  
* **Podstawy Przetwarzania Języka Naturalnego (NLP):** Zdobędziesz praktyczne doświadczenie w analizie tekstu i ekstrakcji informacji (sentymentu).  
* **Zarządzanie Danymi:** Przećwiczysz zapisywanie i odczytywanie danych w popularnych formatach, co jest kluczowe w każdej aplikacji przetwarzającej dane.  
* **Bardziej Złożona Logika:** Rozwiniesz umiejętności strukturyzowania kodu i zarządzania bardziej skomplikowanym przepływem danych.  
* **Potencjał Wizualizacji/UI:** Projekt stwarza naturalną okazję do nauki podstaw wizualizacji danych lub tworzenia prostych interfejsów webowych.  
* **Kontrola Wersji (Git):** Będziesz kontynuować praktykę pracy z Gitem, zarządzając bardziej rozbudowanym projektem.

## **Krok 1: Wiedza Teoretyczna (Rozszerzenie Fundamentów)**

Opierając się na wiedzy z Projektu 1, poszerz swoje horyzonty o następujące zagadnienia:

1. **Praca z Wieloma API:**  
   * **Strategie:** Jak zarządzać różnymi kluczami API, strukturami odpowiedzi i limitami zapytań dla różnych serwisów.  
   * **Refaktoryzacja:** Jak pisać kod, aby łatwo dodawać nowe źródła danych (API) bez przepisywania dużej części logiki.  
   * **Przykładowe API:**  
     * **NewsAPI ([https://newsapi.org/](https://newsapi.org/)):** Popularne API do wiadomości (wymaga darmowej rejestracji dla klucza API). Zwróć uwagę na limity w planie darmowym.  
     * **Alpha Vantage (News & Sentiment Endpoint):** Jeśli nadal używasz Alpha Vantage, sprawdź ich endpoint NEWS\_SENTIMENT. ([https://www.alphavantage.co/documentation/\#news-sentiment](https://www.alphavantage.co/documentation/#news-sentiment))  
     * *Poszukaj też innych darmowych API dostarczających wiadomości finansowe.*  
2. **Podstawy Analizy Sentymentu:**  
   * **Co to jest?** Proces określania emocjonalnego zabarwienia tekstu (pozytywny, negatywny, neutralny).  
   * **Proste Podejścia:**  
     * **Metoda Słownikowa (Lexicon-based):** Tworzenie list słów pozytywnych (np. "wzrost", "dobry", "zyski") i negatywnych (np. "spadek", "zły", "straty") i zliczanie ich wystąpień w tekście.  
     * **Gotowe Biblioteki:**  
       * **VADER (Valence Aware Dictionary and sEntiment Reasoner):** Biblioteka Pythona specjalnie dostosowana do analizy sentymentu w tekstach z mediów społecznościowych, ale dobrze radzi sobie też z innymi typami tekstów. (pip install vaderSentiment)  
       * **TextBlob:** Prosta biblioteka do przetwarzania tekstu, oferująca m.in. analizę sentymentu. (pip install textblob, może wymagać pobrania dodatkowych danych: python \-m textblob.download\_corpora)  
   * **Gdzie się uczyć?**  
     * Wyszukaj tutoriale "Python sentiment analysis tutorial", "VADER sentiment analysis Python", "TextBlob sentiment analysis". Jest wiele artykułów i filmów na ten temat.  
3. **Praca z Plikami (CSV/JSON):**  
   * **Moduł csv w Pythonie:** Jak czytać i zapisywać dane w formacie Comma Separated Values.  
   * **Moduł json w Pythonie:** Jak serializować (zapisywać) obiekty Pythona do formatu JSON i deserializować (wczytywać) JSON z powrotem do obiektów Pythona.  
   * **Kluczowe koncepty:** Struktura plików CSV (wiersze, kolumny, separator), struktura JSON (obiekty, tablice, klucze, wartości), tryby otwierania plików ('r', 'w', 'a').  
4. **(Opcjonalnie) Podstawy Baz Danych (SQLite):**  
   * **Co to jest SQLite?** Lekka, plikowa baza danych, idealna do małych projektów, nie wymaga osobnego serwera.  
   * **Moduł sqlite3 w Pythonie:** Jak tworzyć połączenie, wykonywać zapytania SQL (CREATE TABLE, INSERT, SELECT).  
   * **Podstawy SQL:** Zrozumienie podstawowych poleceń SQL do tworzenia tabel i manipulowania danymi.  
5. **(Opcjonalnie) Podstawy Wizualizacji/Web Frameworków:**  
   * **Matplotlib/Seaborn:** Biblioteki do tworzenia wykresów w Pythonie.  
   * **Flask/Streamlit:** Lekkie frameworki webowe w Pythonie, pozwalające na szybkie tworzenie prostych aplikacji webowych do prezentacji danych.

## **Krok 2: Przygotowanie Narzędzi**

Potrzebujesz narzędzi z Projektu 1 oraz potencjalnie:

1. **Klucze API** do wybranych serwisów informacyjnych (np. NewsAPI).  
2. **Zainstalowane biblioteki Pythona:** requests, vaderSentiment lub textblob (jeśli zdecydujesz się ich użyć), ewentualnie matplotlib, flask, streamlit. (pip install ...)

## **Krok 3: Budowa Agregatora Nastrojów (Wskazówki)**

Stwórz nowy folder dla projektu (np. Projekt\_02\_Agregator\_Nastrojow) i zainicjuj w nim repozytorium Git (git init). Główny kod pisz w pliku sentiment\_aggregator.py. Pamiętaj o regularnym używaniu git add i git commit.

1. **Konfiguracja:**  
   * Zdefiniuj listę symboli do analizy.  
   * Bezpiecznie skonfiguruj klucze API (użyj zmiennych środowiskowych lub pliku .env \- dodaj go do .gitignore\!).  
   * Zdefiniuj nazwy plików do zapisu danych (np. sentiment\_data.csv).  
   * Skonfiguruj logowanie (logging).  
   * *Commit: "Initial setup, configuration, and logging"*  
2. **Pobieranie Danych z Wielu API (Twoje Zadanie\!):**  
   * Napisz funkcje do pobierania danych z *każdego* wybranego API. Każda funkcja powinna przyjmować symbol i klucz API jako argumenty.  
   * Zadbaj o spójny format zwracanych danych (np. lista słowników, gdzie każdy słownik reprezentuje jeden nagłówek i zawiera np. 'symbol', 'source\_api', 'published\_at', 'headline', 'url'). Ujednolić format daty/czasu.  
   * Obsłuż błędy specyficzne dla każdego API (limity zapytań, błędy autentykacji, brak wyników).  
   * Stwórz główną funkcję fetch\_all\_news(symbols, api\_configs), która wywoła funkcje dla poszczególnych API i połączy wyniki w jedną listę.  
   * *Commit: "Implemented functions to fetch news from \[API\_1\_Name\] and \[API\_2\_Name\]"*  
   * *Commit: "Created main function to aggregate news from all sources"*  
3. **Analiza Sentymentu (Twoje Zadanie\!):**  
   * Wybierz metodę analizy sentymentu (słownikowa lub biblioteka).  
   * Napisz funkcję analyze\_sentiment(text), która przyjmuje tekst nagłówka i zwraca wynik sentymentu (np. 'positive', 'negative', 'neutral' lub wynik liczbowy, np. z VADER).  
   * Zintegruj tę funkcję z procesem przetwarzania pobranych nagłówków. Dodaj wynik sentymentu do każdego słownika reprezentującego nagłówek.  
   * **Wskazówka (VADER):**  
```python
     from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer

     analyzer = SentimentIntensityAnalyzer()

     def analyze_sentiment_vader(text):  
         vs = analyzer.polarity_scores(text)  
         # compound score ranges from -1 (most negative) to +1 (most positive)  
         if vs['compound'] >= 0.05:  
             return 'positive', vs['compound']  
         elif vs['compound'] <= -0.05:  
             return 'negative', vs['compound']  
         else:  
             return 'neutral', vs['compound']

     # Przykład użycia:  
     # sentiment_label, sentiment_score = analyze_sentiment_vader("Stock price surges on positive earnings report!")
```
   * *Commit: "Implemented sentiment analysis function using \[Method/Library\]"*  
   * *Commit: "Integrated sentiment analysis into news processing workflow"*  
4. **Agregacja Wyników (Twoje Zadanie\!):**  
   * Napisz funkcję calculate\_aggregate\_sentiment(news\_list), która grupuje przeanalizowane nagłówki według symbolu.  
   * Dla każdego symbolu oblicz zagregowany wskaźnik, np.:  
     * Procent nagłówków pozytywnych.  
     * Procent nagłówków negatywnych.  
     * Średni wynik sentymentu (jeśli używasz wyniku liczbowego).  
   * Zwróć wyniki w czytelnej strukturze (np. słownik, gdzie kluczem jest symbol).  
   * *Commit: "Implemented function to calculate aggregate sentiment per symbol"*  
5. **Zapisywanie Danych (Twoje Zadanie\!):**  
   * Napisz funkcję save\_results\_to\_csv(data, filename), która zapisze szczegółowe wyniki analizy (lista słowników z nagłówkami i ich sentymentem) do pliku CSV. Pamiętaj o dodaniu nagłówków kolumn. Rozważ tryb dopisywania ('a'), aby nie nadpisywać danych przy każdym uruchomieniu, ale dodawać nowe. Dodaj kolumnę z datą/czasem zapisu.  
   * Alternatywnie, użyj formatu JSON.  
   * *Commit: "Implemented function to save detailed analysis results to CSV/JSON"*  
6. **Prezentacja Podsumowania (Twoje Zadanie\!):**  
   * Sformatuj zagregowane wyniki sentymentu (z kroku 4\) w czytelny sposób.  
   * Wyświetl podsumowanie na konsoli używając logging.info() lub print().  
   * Opcjonalnie: Zapisz podsumowanie do osobnego pliku tekstowego.  
   * *Commit: "Added functionality to display/save aggregated sentiment summary"*  
7. **Główny Przepływ Skryptu:**  
   * Połącz wszystkie funkcje w logiczny przepływ w bloku if \_\_name\_\_ \== "\_\_main\_\_":.  
   * Dodaj obsługę błędów na głównym poziomie (np. jeśli nie uda się pobrać żadnych wiadomości).  
8. **Testowanie i Debugowanie:**  
   * Testuj każdą funkcję osobno.  
   * Sprawdzaj zawartość plików wyjściowych.  
   * Monitoruj logi.  
   * Zwracaj uwagę na limity API.

## **Krok 4: Co Dalej? (Opcjonalne Pomysły na Rozwój)**

* **Wizualizacja:** Użyj matplotlib lub seaborn, aby stworzyć wykresy pokazujące zmianę zagregowanego sentymentu w czasie (wymaga regularnego uruchamiania skryptu i odczytu historii z pliku).  
* **Interfejs Webowy:** Stwórz prostą aplikację webową (np. w Flask lub Streamlit), która będzie prezentować aktualne podsumowanie sentymentu i ewentualnie historię.  
* **Baza Danych:** Zamiast plików CSV/JSON, użyj bazy danych SQLite do przechowywania wyników analizy. Pozwoli to na łatwiejsze wykonywanie zapytań i analizę historyczną.  
* **Bardziej Zaawansowany NLP:** Zamiast prostej analizy sentymentu, spróbuj ekstrakcji encji (np. nazw firm, osób wymienionych w nagłówkach) używając bibliotek takich jak spaCy lub NLTK.  
* **Filtrowanie Źródeł:** Dodaj możliwość filtrowania wiadomości według źródła lub wiarygodności (jeśli API dostarcza takie informacje).  
* **Automatyzacja (Cloud):** Wdrażaj skrypt jako funkcję w chmurze (np. Azure Functions) z wyzwalaczem czasowym, aby działał automatycznie i zapisywał wyniki np. do Azure Table Storage lub Cosmos DB.

**Ważna Uwaga Końcowa (Disclaimer)**

Podobnie jak Projekt 1, ten projekt ma charakter **wyłącznie edukacyjny**. Analiza sentymentu oparta na nagłówkach jest bardzo uproszczonym wskaźnikiem i **nie powinna być podstawą do podejmowania decyzji inwestycyjnych**. Nastroje rynkowe są złożone, a wiadomości mogą być mylące lub opóźnione. Inwestowanie zawsze wiąże się z ryzykiem.

Powodzenia w budowie Agregatora Nastrojów Rynkowych\!
