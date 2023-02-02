
1. Find the model number, speed and hard drive capacity for all the PCs with prices below $500.
Result set: model, speed, hd.

SELECT model, speed, hd
FROM PC
WHERE price<$500;

2. Find the model number, RAM and screen size of the laptops with prices over $1000.

SELECT model number, RAM, screen size FROM laptop
WHERE  price > $1000;

3. Find all records from the Printer table containing data about color printers.

SELECT * FROM Printer
WHERE color = ('y');

4. Find the model number, speed and hard drive capacity of PCs cheaper than $600 having a 12x or a 24x CD drive.

SELECT model, speed, hd
FROM PC
WHERE (CD ='12x' OR CD='24x')
AND price<600

5. List all printer makers. Result set: maker.

SELECT DISTINCT maker AS Maker
FROM Product
WHERE TYPE = 'Printer'

6. For each maker producing laptops with a hard drive capacity of 10 Gb or higher, find the speed of such laptops. Result set: maker, speed.

SELECT DISTINCT Product.maker, Laptop.speed
FROM Product LEFT JOIN Laptop 
ON Laptop.model = Product.model
WHERE hd >= 10

7.Get the models and prices for all commercially available products (of any type) produced by maker B.

SELECT Product.model, PC.price
FROM PC INNER JOIN Product
ON PC.model=Product.model
WHERE Product.maker='B'
UNION
SELECT Product.model, Laptop.price
FROM Laptop INNER JOIN Product
ON Laptop.model=Product.model
WHERE Product.maker='B'
UNION
SELECT Product.model, Printer.price
FROM Printer INNER JOIN Product
ON Printer.model=Product.model
WHERE Product.maker='B'



