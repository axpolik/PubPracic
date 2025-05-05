# **Projekt 3: System Wypożyczalni Samochodów Web**

Po opanowaniu pracy z API i podstaw analizy danych, czas na zbudowanie pełnoprawnej aplikacji webowej z bazą danych. Twoim zadaniem w tym projekcie będzie stworzenie systemu obsługi dla fikcyjnej wypożyczalni samochodów. Aplikacja będzie wspierać kluczowe procesy biznesowe firmy i będzie dostępna dla pracowników przez przeglądarkę internetową.

Projekt ten pozwoli Ci zanurzyć się w świat tworzenia aplikacji webowych w Pythonie, zarządzania bazami danych, implementacji logiki biznesowej oraz obsługi różnych ról użytkowników. Zdobędziesz praktyczne doświadczenie w technologiach i koncepcjach fundamentalnych dla wielu systemów informatycznych, w tym tych budowanych na platformie Microsoft Azure.

## **Co Zbudujesz?**

Aplikację webową ("System Wypożyczalni"), która umożliwi:

1. **Zarządzanie Flotą Samochodów (Rola: Operator):**  
   * Dodawanie nowych samochodów do bazy (marka, model, rok produkcji, numer rejestracyjny, cena za dobę, status np. dostępny/wypożyczony/w serwisie).  
   * Modyfikowanie danych istniejących samochodów.  
   * Usuwanie samochodów (tylko jeśli nie mają historii wypożyczeń).  
   * Przyjmowanie samochodów po wypożyczeniu: rejestrowanie daty zwrotu i opisu stanu technicznego (np. uwagi o uszkodzeniach).  
2. **Obsługę Klientów i Wypożyczeń (Rola: Sprzedawca):**  
   * Wyszukiwanie klientów w bazie danych.  
   * Sprawdzanie statusu klienta (np. czy nie jest zablokowany).  
   * Dodawanie nowych klientów do bazy (imię, nazwisko, dane kontaktowe, numer dokumentu).  
   * Przeglądanie dostępnych samochodów (z możliwością filtrowania/sortowania).  
   * Sprawdzanie przewidywanej daty zwrotu dla samochodów aktualnie wypożyczonych.  
   * Rejestrowanie nowego wypożyczenia (wybór klienta, samochodu, ustalenie daty początkowej i końcowej).  
   * Finalizowanie zwrotu samochodu: potwierdzanie zwrotu po odbiorze technicznym przez Operatora, obliczanie ostatecznej kwoty do zapłaty (uwzględniając ewentualne opóźnienia lub zmiany).  
   * Przeglądanie historii wypożyczeń dla konkretnego samochodu lub klienta.  
   * Aktualizowanie informacji o wypożyczeniu (np. zmiana planowanej daty zwrotu przez klienta, dodanie notatki).  
3. **Podstawową Obsługę Ról:** Logowanie użytkowników i ograniczenie dostępu do poszczególnych funkcji w zależności od roli (Operator/Sprzedawca).

## **Dlaczego Ten Projekt?**

* **Praktyczne Tworzenie Aplikacji Webowych:** Zastosujesz popularny framework webowy Pythona (np. Flask lub Django) do zbudowania działającej aplikacji.  
* **Modelowanie i Zarządzanie Bazą Danych:** Zaprojektujesz strukturę relacyjnej bazy danych i nauczysz się nią zarządzać za pomocą ORM (Object-Relational Mapping).  
* **Implementacja Logiki Biznesowej:** Przetłumaczysz wymagania biznesowe na konkretne funkcje i reguły w kodzie (np. sprawdzanie dostępności, obliczanie cen).  
* **Uwierzytelnianie i Autoryzacja:** Zrozumiesz i zaimplementujesz podstawowe mechanizmy kontroli dostępu w aplikacji webowej.  
* **Operacje CRUD:** Przećwiczysz tworzenie, odczytywanie, aktualizowanie i usuwanie danych (CRUD) w kontekście aplikacji webowej.  
* **Podstawy Front-endu:** Stworzysz proste interfejsy użytkownika przy użyciu HTML i ewentualnie podstaw CSS.  
* **Kompleksowe Rozwiązywanie Problemów:** Zmierzysz się z wyzwaniami integracji różnych komponentów (backend, frontend, baza danych).  
* **Kontrola Wersji (Git):** Utrwalisz dobre praktyki pracy z Gitem w bardziej złożonym projekcie.

## **Krok 1: Wiedza Teoretyczna (Nowe Obszary)**

Oprócz wiedzy z poprzednich projektów, skup się na:

1. **Frameworki Webowe w Pythonie:**  
   * **Co to jest?** Narzędzia ułatwiające tworzenie aplikacji webowych, zarządzające routingiem (obsługą adresów URL), szablonami (generowaniem HTML) i obsługą żądań HTTP.  
   * **Popularne Wybory:**  
     * **Flask:** Mikroframework, elastyczny i dobry na start, wymaga doboru dodatkowych komponentów (np. ORM).  
     * **Django:** Framework "batteries-included", oferuje wiele wbudowanych narzędzi (ORM, panel admina, system uwierzytelniania), bardziej rozbudowany, ale prowadzi za rękę.  
   * **Kluczowe Koncepty:** Routing, widoki (views/controllers), szablony (templates \- np. Jinja2 dla Flaska, Django Templates), żądania (request), odpowiedzi (response), sesje.  
   * **Gdzie się uczyć?** Oficjalna dokumentacja wybranego frameworka, tutoriale online (np. na Real Python, YouTube, FreeCodeCamp).  
2. **Relacyjne Bazy Danych i SQL:**  
   * **Podstawy:** Tabele, kolumny, typy danych, klucze główne (primary key), klucze obce (foreign key), relacje (jeden-do-wielu, wiele-do-wielu).  
   * **Podstawowe Zapytania SQL:** SELECT, INSERT, UPDATE, DELETE, CREATE TABLE. Nawet jeśli będziesz używać ORM, podstawowa znajomość SQL jest bardzo pomocna.  
   * **Wybór Bazy Danych:**  
     * **SQLite:** Prosta, plikowa baza danych, idealna do nauki i małych projektów (wbudowana w Pythona).  
     * **PostgreSQL/MySQL:** Bardziej zaawansowane, serwerowe bazy danych, często używane w produkcyjnych aplikacjach.  
3. **ORM (Object-Relational Mapping):**  
   * **Co to jest?** Technika pozwalająca na interakcję z bazą danych za pomocą obiektów Pythona zamiast pisania surowego SQL. Mapuje klasy Pythona na tabele w bazie danych.  
   * **Popularne Wybory:**  
     * **SQLAlchemy:** Potężny i popularny ORM, często używany z Flaskiem.  
     * **Django ORM:** Wbudowany w Django, ściśle zintegrowany z resztą frameworka.  
   * **Kluczowe Koncepty:** Modele (klasy reprezentujące tabele), sesje/menedżery zapytań, migracje (zarządzanie zmianami w strukturze bazy danych \- np. za pomocą Alembic dla SQLAlchemy lub wbudowanych migracji Django).  
4. **Podstawy HTML i CSS:**  
   * **HTML:** Struktura strony internetowej (znaczniki \<div\>, \<form\>, \<input\>, \<table\>, \<a\> itp.).  
   * **CSS:** Stylowanie strony (wygląd, kolory, układ). Można zacząć od bardzo podstawowych stylów lub użyć prostego frameworka CSS jak Bootstrap czy Tailwind CSS (choć to może być krok na później).  
5. **Uwierzytelnianie i Autoryzacja:**  
   * **Uwierzytelnianie (Authentication):** Weryfikacja tożsamości użytkownika (kto to jest? \- np. logowanie hasłem).  
   * **Autoryzacja (Authorization):** Sprawdzanie uprawnień zalogowanego użytkownika (co może zrobić? \- np. dostęp do funkcji Operatora/Sprzedawcy).  
   * **Biblioteki:** Flask-Login, Flask-Security, wbudowany system auth w Django.

## **Krok 2: Przygotowanie Narzędzi**

1. **Python 3** i menedżer pakietów pip.  
2. **Visual Studio Code** z rozszerzeniem Python.  
3. **Git**.  
4. **Wybrany framework webowy:** Flask lub Django (pip install Flask lub pip install Django).  
5. **Wybrany ORM i narzędzia powiązane:**  
   * Jeśli Flask: pip install Flask-SQLAlchemy alembic (Alembic do migracji).  
   * Jeśli Django: ORM jest wbudowany.  
6. **Przeglądarka internetowa.**  
7. **(Opcjonalnie) Klient Bazy Danych:** Narzędzie graficzne do przeglądania bazy (np. DB Browser for SQLite, DBeaver).

## **Krok 3: Budowa Systemu (Wskazówki z Przykładami Kodu \- Flask/SQLAlchemy)**

Stwórz nowy folder projektu, zainicjuj repozytorium Git. Struktura projektu będzie zależeć od wybranego frameworka. Poniższe przykłady zakładają użycie Flask i Flask-SQLAlchemy.

1. **Inicjalizacja Projektu i Bazy Danych:**  
   * Skonfiguruj podstawową strukturę projektu Flask (np. plik app.py, folder templates).  
   * Skonfiguruj połączenie z bazą danych w app.py:  
```python
     from flask import Flask  
     from flask_sqlalchemy import SQLAlchemy  
     import os

     # Pobranie ścieżki do bieżącego katalogu  
     basedir = os.path.abspath(os.path.dirname(__file__))

     app = Flask(__name__)  
     # Konfiguracja klucza sekretnego (ważne dla sesji, formularzy)  
     app.config['SECRET_KEY'] = 'twoj_bardzo_sekretny_klucz'  
     # Konfiguracja ścieżki do bazy danych SQLite  
     app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///' + os.path.join(basedir, 'rental.db')  
     # Wyłączenie śledzenia modyfikacji (może zużywać dodatkowe zasoby)  
     app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

     # Inicjalizacja rozszerzenia SQLAlchemy  
     db = SQLAlchemy(app)

     # Tutaj będą definicje modeli i widoków...

     if __name__ == '__main__':  
         # Uruchomienie aplikacji w trybie debugowania  
         app.run(debug=True)
```
   * Zainicjuj system migracji Alembic (w terminalu, w folderze projektu): alembic init migrations (po zainstalowaniu alembic), a następnie skonfiguruj alembic.ini i migrations/env.py, aby wskazywały na Twoją aplikację i modele.  
   * *Commit: "Initial project setup with Flask and SQLAlchemy configuration"*  
2. **Modelowanie Danych (ORM):**  
   * Zdefiniuj modele w pliku (np. models.py i zaimportuj db z app.py lub zdefiniuj bezpośrednio w app.py):  
```python
     from app import db # Załóżmy, że db jest w app.py  
     from datetime import datetime  
     from werkzeug.security import generate_password_hash, check_password_hash

     class User(db.Model):  
         id = db.Column(db.Integer, primary_key=True)  
         username = db.Column(db.String(64), index=True, unique=True, nullable=False)  
         password_hash = db.Column(db.String(128))  
         role = db.Column(db.String(10), nullable=False) # 'Operator' lub 'Sprzedawca'

         def set_password(self, password):  
             self.password_hash = generate_password_hash(password)

         def check_password(self, password):  
             return check_password_hash(self.password_hash, password)

     class Car(db.Model):  
         id = db.Column(db.Integer, primary_key=True)  
         make = db.Column(db.String(50), nullable=False) # Marka  
         model = db.Column(db.String(50), nullable=False)  
         year = db.Column(db.Integer)  
         license_plate = db.Column(db.String(10), unique=True, nullable=False) # Nr rej.  
         price_per_day = db.Column(db.Float, nullable=False)  
         status = db.Column(db.String(20), default='dostępny', nullable=False) # np. dostępny, wypożyczony, w_serwisie  
         technical_notes = db.Column(db.Text) # Uwagi techniczne  
         # Relacja do wypożyczeń (jeden samochód może mieć wiele wypożyczeń)  
         rentals = db.relationship('Rental', backref='car', lazy='dynamic')

     class Customer(db.Model):  
         id = db.Column(db.Integer, primary_key=True)  
         first_name = db.Column(db.String(50), nullable=False)  
         last_name = db.Column(db.String(50), nullable=False)  
         email = db.Column(db.String(120), index=True, unique=True)  
         phone = db.Column(db.String(15))  
         document_id = db.Column(db.String(20), unique=True) # Nr dokumentu  
         status = db.Column(db.String(20), default='aktywny', nullable=False) # np. aktywny, zablokowany  
         # Relacja do wypożyczeń  
         rentals = db.relationship('Rental', backref='customer', lazy='dynamic')

     class Rental(db.Model):  
         id = db.Column(db.Integer, primary_key=True)  
         car_id = db.Column(db.Integer, db.ForeignKey('car.id'), nullable=False)  
         customer_id = db.Column(db.Integer, db.ForeignKey('customer.id'), nullable=False)  
         start_date = db.Column(db.DateTime, default=datetime.utcnow, nullable=False)  
         planned_end_date = db.Column(db.DateTime, nullable=False)  
         actual_end_date = db.Column(db.DateTime) # Uzupełniane przy zwrocie  
         initial_cost = db.Column(db.Float) # Obliczany przy wypożyczeniu  
         final_cost = db.Column(db.Float) # Obliczany przy zwrocie  
         operator_notes = db.Column(db.Text) # Uwagi operatora po zwrocie  
         sales_notes = db.Column(db.Text) # Uwagi sprzedawcy (np. powód przedłużenia)  
         status = db.Column(db.String(20), default='aktywne', nullable=False) # np. aktywne, zakończone
```
   * Wygeneruj migrację: alembic revision \--autogenerate \-m "Utworzenie modeli User, Car, Customer, Rental"  
   * Zastosuj migrację: alembic upgrade head  
   * *Commit: "Defined database models for User, Car, Customer, Rental using SQLAlchemy"*  
   * *Commit: "Generated and applied initial database migration with Alembic"*  
3. **Uwierzytelnianie i Role (Przykład z Flask-Login):**  
   * Zainstaluj: pip install Flask-Login  
   * Skonfiguruj Flask-Login w app.py:  
```python
     from flask_login import LoginManager, UserMixin, login_user, logout_user, login_required, current_user

     # ... (konfiguracja app i db)

     login_manager = LoginManager(app)  
     login_manager.login_view = 'login' # Nazwa widoku logowania

     # Zmodyfikuj model User, aby dziedziczył z UserMixin  
     class User(UserMixin, db.Model):  
         # ... (reszta definicji modelu User)  
         pass # UserMixin dodaje wymagane atrybuty (is_authenticated, etc.)

     @login_manager.user_loader  
     def load_user(id):  
         # Funkcja wymagana przez Flask-Login do ładowania użytkownika z sesji  
         return User.query.get(int(id))

     # Przykład widoku logowania  
     from flask import render_template, request, redirect, url_for, flash  
     from werkzeug.security import check_password_hash

     @app.route('/login', methods=['GET', 'POST'])  
     def login():  
         if current_user.is_authenticated: # Jeśli już zalogowany, przekieruj  
             return redirect(url_for('index')) # Załóżmy, że 'index' to główna strona  
         if request.method == 'POST':  
             username = request.form['username']  
             password = request.form['password']  
             user = User.query.filter_by(username=username).first()  
             if user is None or not user.check_password(password):  
                 flash('Nieprawidłowa nazwa użytkownika lub hasło')  
                 return redirect(url_for('login'))  
             login_user(user) # Zaloguj użytkownika (Flask-Login zapisze go w sesji)  
             flash('Zalogowano pomyślnie!')  
             # Można przekierować na inną stronę w zależności od roli  
             # if user.role == 'Operator': ...  
             return redirect(url_for('index'))  
         return render_template('login.html') # Szablon z formularzem logowania

     @app.route('/logout')  
     @login_required # Wymaga zalogowania  
     def logout():  
         logout_user()  
         flash('Wylogowano pomyślnie.')  
         return redirect(url_for('login'))

     # Przykład dekoratora sprawdzającego rolę  
     from functools import wraps

     def role_required(role_name):  
         def decorator(f):  
             @wraps(f)  
             def decorated_function(*args, **kwargs):  
                 if not current_user.is_authenticated:  
                     return redirect(url_for('login'))  
                 if current_user.role != role_name:  
                     flash(f'Brak uprawnień. Wymagana rola: {role_name}')  
                     return redirect(url_for('index')) # Lub strona błędu  
                 return f(*args, **kwargs)  
             return decorated_function  
         return decorator

     @app.route('/admin/cars')  
     @login_required  
     @role_required('Operator') # Tylko Operator ma dostęp  
     def manage_cars():  
         # Logika widoku zarządzania samochodami  
         return "Strona zarządzania samochodami (tylko dla Operatora)"

     @app.route('/')  
     @login_required # Wszyscy zalogowani mogą wejść na stronę główną  
     def index():  
         return f"Witaj {current_user.username}! Twoja rola: {current_user.role}"
```
   * *Commit: "Implemented basic user authentication with Flask-Login"*  
   * *Commit: "Added role checking decorator and secured example view"*  
4. **Funkcjonalności Operatora (Przykład: Lista Samochodów i Dodawanie):**  
   * Widok w app.py:  
```python
     from models import Car # Załóżmy, że modele są w models.py  
     from forms import AddCarForm # Załóżmy, że używamy Flask-WTF do formularzy

     @app.route('/operator/cars', methods=['GET', 'POST'])  
     @login_required  
     @role_required('Operator')  
     def operator_cars():  
         form = AddCarForm() # Utwórz instancję formularza  
         if form.validate_on_submit(): # Jeśli formularz został wysłany i jest poprawny  
             new_car = Car(  
                 make=form.make.data,  
                 model=form.model.data,  
                 year=form.year.data,  
                 license_plate=form.license_plate.data,  
                 price_per_day=form.price_per_day.data  
                 # status domyślnie 'dostępny'  
             )  
             try:  
                 db.session.add(new_car)  
                 db.session.commit()  
                 flash('Dodano nowy samochód!', 'success')  
                 return redirect(url_for('operator_cars'))  
             except Exception as e:  
                 db.session.rollback() # Wycofaj zmiany w razie błędu  
                 flash(f'Błąd podczas dodawania samochodu: {e}', 'danger')

         # Pobierz wszystkie samochody (można dodać filtrowanie/sortowanie)  
         cars = Car.query.filter(Car.status != 'usunięty').order_by(Car.make, Car.model).all()  
         return render_template('operator_cars.html', cars=cars, form=form)
```
   * Szablon templates/operator\_cars.html (używając Jinja2):  
```Jinja2
     {% extends "base.html" %} {% block content %}  
     <h1>Zarządzanie Samochodami (Operator)</h1>

     {% with messages = get_flashed_messages(with_categories=true) %}  
       {% if messages %}  
         {% for category, message in messages %}  
           <div class="alert alert-{{ category }}">{{ message }}</div>  
         {% endfor %}  
       {% endif %}  
     {% endwith %}

     <h2>Dodaj Nowy Samochód</h2>  
     <form method="POST" action="{{ url_for('operator_cars') }}">  
         {{ form.hidden_tag() }} <p>  
             {{ form.make.label }}<br>  
             {{ form.make(size=30) }}<br>  
             {% for error in form.make.errors %}  
             <span style="color: red;">[{{ error }}]</span>  
             {% endfor %}  
         </p>  
         <p>  
             {{ form.model.label }}<br>  
             {{ form.model(size=30) }}<br>  
             {% for error in form.model.errors %}  
             <span style="color: red;">[{{ error }}]</span>  
             {% endfor %}  
         </p>  
         <p>{{ form.submit() }}</p>  
     </form>

     <h2>Lista Samochodów</h2>  
     <table>  
         <thead>  
             <tr>  
                 <th>Marka</th>  
                 <th>Model</th>  
                 <th>Rok</th>  
                 <th>Nr Rej.</th>  
                 <th>Cena/Doba</th>  
                 <th>Status</th>  
                 <th>Akcje</th>  
             </tr>  
         </thead>  
         <tbody>  
             {% for car in cars %}  
             <tr>  
                 <td>{{ car.make }}</td>  
                 <td>{{ car.model }}</td>  
                 <td>{{ car.year }}</td>  
                 <td>{{ car.license_plate }}</td>  
                 <td>{{ "%.2f"|format(car.price_per_day) }} zł</td>  
                 <td>{{ car.status }}</td>  
                 <td>  
                     <a href="{{ url_for('edit_car', car_id=car.id) }}">Edytuj</a>  
                     <a href="{{ url_for('delete_car', car_id=car.id) }}" onclick="return confirm('Czy na pewno usunąć?')">Usuń</a>  
                 </td>  
             </tr>  
             {% else %}  
             <tr>  
                 <td colspan="7">Brak samochodów w bazie.</td>  
             </tr>  
             {% endfor %}  
         </tbody>  
     </table>  
     {% endblock %}
```
   * Potrzebujesz jeszcze zdefiniować AddCarForm używając Flask-WTF (pip install Flask-WTF) oraz widoki edit\_car i delete\_car.  
   * *Commit: "Implemented Car list view and add form for Operator role"*  
5. **Funkcjonalności Sprzedawcy (Przykład: Tworzenie Wypożyczenia):**  
   * Widok w app.py:  
```python
     from models import Customer, Rental  
     from forms import NewRentalForm  
     from datetime import datetime, timedelta

     @app.route('/sales/rentals/new', methods=['GET', 'POST'])  
     @login_required  
     @role_required('Sprzedawca')  
     def new_rental():  
         form = NewRentalForm()  
         # Dynamiczne wypełnienie pól select (klienci, dostępne samochody)  
         form.customer.choices = [(c.id, f"{c.first_name} {c.last_name} ({c.email})") for c in Customer.query.filter_by(status='aktywny').all()]  
         form.car.choices = [(car.id, f"{car.make} {car.model} ({car.license_plate}) - {car.price_per_day:.2f} zł/doba") for car in Car.query.filter_by(status='dostępny').all()]

         if form.validate_on_submit():  
             customer_id = form.customer.data  
             car_id = form.car.data  
             start_date_str = form.start_date.data # Zakładamy, że formularz zwraca string  
             end_date_str = form.end_date.data

             try:  
                 # Konwersja dat i walidacja  
                 start_date = datetime.strptime(start_date_str, '%Y-%m-%d')  
                 end_date = datetime.strptime(end_date_str, '%Y-%m-%d')  
                 if end_date <= start_date:  
                     flash('Data zwrotu musi być późniejsza niż data wypożyczenia.', 'warning')  
                     return render_template('new_rental.html', form=form)

                 # Sprawdzenie dostępności samochodu (ponownie, na wszelki wypadek)  
                 car = Car.query.get_or_404(car_id)  
                 if car.status != 'dostępny':  
                      flash(f'Samochód {car.make} {car.model} nie jest już dostępny.', 'danger')  
                      return redirect(url_for('new_rental')) # Odśwież formularz

                 # Obliczenie wstępnego kosztu  
                 rental_days = (end_date - start_date).days + 1 # +1 bo liczymy też dzień startowy  
                 initial_cost = rental_days * car.price_per_day

                 # Utworzenie nowego wypożyczenia  
                 rental = Rental(  
                     customer_id=customer_id,  
                     car_id=car_id,  
                     start_date=start_date,  
                     planned_end_date=end_date,  
                     initial_cost=initial_cost,  
                     status='aktywne'  
                 )  
                 # Zmiana statusu samochodu  
                 car.status = 'wypożyczony'

                 db.session.add(rental)  
                 db.session.add(car) # Zapisz też zmianę statusu samochodu  
                 db.session.commit()

                 flash(f'Samochód {car.make} {car.model} wypożyczony klientowi ID {customer_id}. Koszt wstępny: {initial_cost:.2f} zł', 'success')  
                 return redirect(url_for('active_rentals')) # Przekieruj do listy aktywnych wypożyczeń

             except ValueError:  
                  flash('Nieprawidłowy format daty. Użyj YYYY-MM-DD.', 'danger')  
             except Exception as e:  
                 db.session.rollback()  
                 flash(f'Wystąpił błąd podczas tworzenia wypożyczenia: {e}', 'danger')

         return render_template('new_rental.html', form=form)
```
   * Potrzebujesz szablonu templates/new\_rental.html z odpowiednim formularzem (NewRentalForm zdefiniowanym w forms.py używając Flask-WTF, zawierającym pola typu SelectField dla klienta i samochodu oraz DateField lub StringField dla dat).  
   * *Commit: "Implemented new rental creation form and logic for Salesperson"*  
6. **Podstawowy Interfejs Użytkownika:**  
   * Stwórz plik templates/base.html z podstawową strukturą HTML, nagłówkiem, stopką i blokiem {% block content %}{% endblock %}. Pozostałe szablony będą go dziedziczyć ({% extends "base.html" %}).  
   * Dodaj prostą nawigację (np. listę linków) w base.html, która może się różnić w zależności od tego, czy użytkownik jest zalogowany i jaką ma rolę ({% if current\_user.is\_authenticated %} ... {% if current\_user.role \== 'Operator' %}).  
7. **Testowanie:**  
   * Uruchom aplikację (flask run lub python app.py).  
   * Przeklikaj wszystkie funkcjonalności dla obu ról.  
   * Sprawdzaj poprawność danych w bazie (np. używając DB Browser for SQLite).  
   * Testuj przypadki brzegowe (np. próba usunięcia wypożyczonego samochodu, podanie błędnych dat).

## **Krok 4: Co Dalej? (Opcjonalne Pomysły na Rozwój)**

* **Rozbudowane Cenniki:** Wprowadź różne stawki cenowe w zależności od klasy samochodu, długości wypożyczenia, sezonu itp.  
* **Raportowanie:** Dodaj moduł generujący proste raporty (np. najbardziej popularne samochody, przychody w danym okresie).  
* **Ulepszony Interfejs Użytkownika:** Zastosuj framework CSS (Bootstrap, Tailwind) dla lepszego wyglądu, dodaj elementy JavaScript dla większej interaktywności (np. dynamiczne filtrowanie, wybieranie dat z kalendarza).  
* **Powiadomienia:** Implementacja powiadomień (np. email) o zbliżającym się terminie zwrotu.  
* **Zarządzanie Serwisem:** Dodaj moduł do śledzenia przeglądów technicznych i napraw samochodów.  
* **API:** Udostępnij niektóre funkcjonalności (np. sprawdzanie dostępności) przez API RESTowe (np. używając Flask-RESTful lub Django REST Framework).  
* **Testy Automatyczne:** Napisz testy jednostkowe i integracyjne dla swojej aplikacji (np. używając pytest).  
* **Wdrożenie (Deployment):** Spróbuj wdrożyć swoją aplikację na platformie hostingowej (np. Heroku, PythonAnywhere, a docelowo Azure App Service).

**Ważna Uwaga Końcowa (Disclaimer)**

Ten projekt, mimo że oparty na realnym scenariuszu biznesowym, ma charakter **edukacyjny**. Zbudowany system będzie uproszczeniem rzeczywistych rozwiązań. Skup się na nauce technologii i dobrych praktyk programistycznych.

Powodzenia w tworzeniu systemu wypożyczalni\! To ambitny, ale bardzo satysfakcjonujący projekt.
