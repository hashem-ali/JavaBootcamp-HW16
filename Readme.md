# SQL Database


### Complete the following steps to complete the project: 


[![123.png](https://i.postimg.cc/wvNyv8fw/123.png)](https://postimg.cc/G8ch7N1D)

###  1️⃣ Create the above database as shown in the image with the following steps : 
1. Create database named " store ".
2. Create table countries. 
3. Create table users. 
3. Create table orders.
4. Create table order_products. 
5. Create table products. 
  

###  2️⃣ Connect tables using foreign keys when applicable

###  3️⃣ Add the following constraints to each tables

1. **countries**
    1. Add unique constraint to column " name ".
    2. Add not null constraint to column " continent_name ".
  
2. **users**
    1. Add unique constraint to column " email ".
    2. Add check constraint to column " gender " between 'm' or 'f'.

3. **orders**
    1. Add check constraint to column " status " between 'start' or 'finish'.

4. **order_items**
    1. Add default value to column " quantity " value 0.

5. **products**
    1. Add default value to column " price " value 0.
    2. Add not null constraint to column " name ".
    3. Add check constraint to column " status " between 'valid' or 'expired'.


**Bouns : Add default datetime to created_at column which take the timestap when the row is created**

### 4️⃣ Write the DML commands for the following instructions ( choose data randomly ) :
1. Add new row to the countries table.
2. Add new row to the users table.
3. Add new row to the orders table.
4. Add new row to the products table.
5. Add new row to the order_products table.
 
6. Update row from countries table.
7. Delete row from products table.

# Answers

## Creating tables and Constrains
create table countries(
    code int primary key ,
    name varchar(20) unique ,
    continent_name varchar(20) not null
);

create table users(
    id int primary key ,
    full_name varchar(20),
    email varchar(20) unique ,
    gender char(1) check ( 'm' or 'f' ),
    date_of_birth varchar(15) ,
    country_code int,
    created_at datetime  default datetime(),
    foreign key (country_code) references countries(code)
);

create table orders(
    id int primary key ,
    status varchar(6) check ( 'start' or 'finish' ),
    user_id int ,
    created_at datetime,
    foreign key (user_id) references users(id)
);

create table order_products(
    order_id int primary key ,
    product_id int ,
    foreign key (product_id) references products(id),
    quantity int default 0
);

create table products(
    id int primary key ,
    name varchar(10) not null ,
    price int default 0,
    status varchar(10) check ( 'valid' or 'expired' ),
    created_at datetime
);
## DML commands
insert into countries (code, name, continent_name) values (1, 'saudi', '966');

insert into users (id, full_name, email, gender, date_of_birth, country_code) values (2, 'hashem ali', 'hashem@gmail.com', 'm', '2020', 1);

insert into orders (id, status, user_id)
values (2, 'start', 2);

insert into order_products (order_id, product_id, quantity) VALUES (1, 2,3);

insert into products (id, name, price, status) values (2, 'hashem', 33, 'valid')
