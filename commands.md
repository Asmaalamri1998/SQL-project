create database store; 
Use store;

CREATE TABLE users( 
id INT PRIMARY KEY,
full_name VARCHAR(20),
email VARCHAR(20),
gender ChAR(1),
datw_of_birth VARCHAR(15),
created_at datetime ,
country_code int); 

CREATE TABLE countries(
code_ INT PRIMARY KEY,
id INT ,
country_name VARCHAR(20),
continent_name VARCHAR (20));

CREATE TABLE orders(
id INT PRIMARY KEY,
user_id INT,
user_status VARCHAR(6),
created_at datetime);

CREATE TABLE products(
id INT PRIMARY KEY,
product_name VARCHAR(10),
price INT,
product_status VARCHAR(10),
created_at datetime);

CREATE TABLE order_products(
id int,
FOREIGN KEY (id) REFERENCES orders(id),
quantity int);
ALTER TABLE order_products
ADD FOREIGN KEY (id) REFERENCES products(id);

ALTER TABLE users
ADD FOREIGN KEY (country_code) REFERENCES countries(code_);

ALTER TABLE orders
ADD FOREIGN KEY (user_id) REFERENCES users(id);

ALTER TABLE countries
ADD CONSTRAINT UNIQUE(country_name);

ALTER TABLE countries
MODIFY continent_name INT NOT NULL;

ALTER TABLE users
ADD CONSTRAINT UNIQUE(email)

ALTER TABLE order_products
ALTER quantity SET DEFAULT '0';

ALTER TABLE products
ALTER price SET DEFAULT '0';

ALTER TABLE products
MODIFY product_name VARCHAR(10) NOT NULL;

ALTER TABLE users
ADD CONSTRAINT gender CHECK (gender='f' or gender='m');

ALTER TABLE orders
ADD CONSTRAINT user_status CHECK (user_status='start' or user_status='finish');

ALTER TABLE products
ADD CONSTRAINT product_status CHECK (product_status='valid' or product_status='expired');

INSERT INTO  countries
VALUES(966,1,'saudi arabia','Asia');

INSERT INTO  users
VALUES(1,'asma','asmaalamri.cs@gmail.com','f','9-10-1998',2022-4-16,966);

INSERT INTO  orders
VALUES(2,1,'start',2022-4-16);

INSERT INTO  products
VALUES(3,'clothes',200,'valid', 2022-4-6);

INSERT INTO  order_products
VALUES(1,2);

UPDATE countries
SET country_name='saudi'
WHERE country_name=' saudi arabia';

DELETE FROM products
WHERE id=3;



