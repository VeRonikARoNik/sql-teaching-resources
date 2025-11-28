# sql-teaching-resources


## Podstawowe komendy SQL

- `CREATE DATABASE` – tworzenie bazy  
- `CREATE TABLE` – tworzenie tabel  
- `INSERT INTO` – dodawanie danych  
- `SELECT` – pobieranie danych  
- `WHERE` – filtrowanie  
- `LIKE` – wyszukiwanie po wzorcu  
- `ORDER BY` – sortowanie  
- `AVG`, `SUM`, `MIN`, `MAX` – agregacje  
- `GROUP BY` – grupowanie  
- `UPDATE` – aktualizacja  
- `DELETE` – usuwanie  
- `JOIN` – łączenie tabel  

---

## Zadanie główne – Sklep internetowy
1. Stwórz bazę danych
```
CREATE DATABASE ShopDB;
USE ShopDB;

```
2. Stwórz tabelę
```
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    category VARCHAR(30),
    price DECIMAL(10,2)
);

```
3. Dodaj dane
```
INSERT INTO products VALUES
(1, 'Laptop', 'Electronics', 3500),
(2, 'Myszka', 'Electronics', 80),
(3, 'Biurko', 'Furniture', 600),
(4, 'Fotel', 'Furniture', 900),
(5, 'Kawa', 'Food', 25);

```

Wyświetlanie danych


```
SELECT * FROM products;

```

Filtrowanie

```
SELECT * FROM products
WHERE category = 'Electronics';

```
Wyszukiwanie po wzorcu
```
SELECT * FROM products
WHERE category = 'Electronics';

```

Sortowanie


```
SELECT * FROM products
ORDER BY price ASC;

```
Funkcje agregujące
```
SELECT AVG(price) FROM products;
SELECT SUM(price) FROM products;
SELECT MAX(price), MIN(price) FROM products;

```
Grupowanie
```
SELECT category, COUNT(*) 
FROM products
GROUP BY category;


```
Aktualizacja danych
```
UPDATE products
SET price = 1000
WHERE name = 'Fotel';
```
Usuwanie danych
```
DELETE FROM products
WHERE id = 5;

```

Zadania

### Wyświetl tylko produkty droższe niż 500 zł.

### Podaj średnią cenę kategorii „Furniture”.

### Policz, ile produktów kosztuje mniej niż 100 zł.

### Wyświetl najdroższy produkt w każdej kategorii.

### Znajdź produkty, których nazwa zawiera literę „a”.

### Usuń produkty tańsze niż 50 zł.

### Podnieś ceny wszystkich mebli o 10%.

### Posortuj produkty malejąco po nazwie.




Zadanie do samodzielnej pracy (20–25 min)
Nowa baza: EmployeeDB
Stwórz tabelę employees z kolumnami:

id, first_name, last_name, department, salary

Dodaj dane:
id	first_name	last_name	department	salary
1	Anna	Nowak	HR	4200
2	Daniel	Kowal	IT	6500
3	Marta	Lewandowska	Sales	5100
4	Igor	Nowicki	IT	7200
5	Olga	Zawadzka	HR	4600


## Polecenia do wykonania

### Wyświetl wszystkich pracowników.

### Znajdź osoby z działu IT.

### Znajdź osoby, których nazwisko zaczyna się na „N”.

### Policz średnią pensję wszystkich pracowników.

### Policz sumę wynagrodzeń w dziale HR.

### Znajdź najwyższą i najniższą pensję.

### Posortuj malejąco po wynagrodzeniu.

### Policz ilu jest pracowników w każdym dziale (GROUP BY).

### Zmień pensję Marty Lewandowskiej na 5500.

### Usuń osobę o id = 1.


Zadanie dodatkowe (trudne) – Relacyjna baza danych

```
CREATE DATABASE OrdersDB;
USE OrdersDB;

```


```
CREATE TABLE customers (
    id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100)
);

```

Stwórz tabele
```
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    product_name VARCHAR(50),
    price DECIMAL(10,2),
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

```

Wstaq dane 
```
INSERT INTO customers VALUES
(1, 'Anna', 'Nowak', 'anna@ex.com'),
(2, 'Marek', 'Zieliński', 'marek@ex.com'),
(3, 'Karolina', 'Wiśniewska', 'karolina@ex.com');

INSERT INTO orders VALUES
(1, 1, 'Laptop', 3200, '2024-03-10'),
(2, 1, 'Myszka', 120, '2024-03-15'),
(3, 2, 'Monitor', 900, '2024-03-12'),
(4, 3, 'Kawa', 25, '2024-03-14');


```


### Wyświetl listę zamówień wraz z imieniem i nazwiskiem klienta (JOIN).

### Wyświetl zamówienia złożone po 12 marca 2024.

### Podaj sumę wartości zamówień każdego klienta.

### Znajdź klienta, który wydał najwięcej pieniędzy.

### Wyświetl tylko zamówienia, których nazwa produktu zaczyna się na „M”.

### Usuń zamówienia o wartości poniżej 50 zł.

### Zmień email Karoliny Wiśniewskiej na „karolina.w@ex.com”.
