#####
# 1 #
#####Найдите номер модели, скорость и размер жесткого диска для всех ПК стоимостью менее 500 дол. Вывести: model, speed и hd.####

SELECT model, speed, hd FROM PC WHERE price < 500

#####
# 2 #
####Найдите производителей принтеров. Вывести: maker.####

SELECT maker FROM Product WHERE type='Printer' GROUP BY maker

#####
# 3 #
####Найдите номер модели, объем памяти и размеры экранов ПК-блокнотов, цена которых превышает 1000 дол.####

SELECT model, ram, screen FROM laptop WHERE price > 1000

#####
# 4 #
###Найдите все записи таблицы Printer для цветных принтеров.###

SELECT * FROM printer WHERE color='y'

#####
# 5 #
####Найдите номер модели, скорость и размер жесткого диска ПК, имеющих 12x или 24x CD и цену менее 600 дол.####

SELECT model, speed, hd FROM PC WHERE (cd='12x' or cd='24x') AND price<600

#####
# 6 #
#####Для каждого производителя, выпускающего ПК-блокноты c объёмом жесткого диска не менее 10 Гбайт, найти скорости таких ПК-блокнотов. Вывод: производитель, скорость.####

SELECT DISTINCT Product.maker, Laptop.speed FROM Product INNER JOIN Laptop ON Product.model=Laptop.model and Laptop.hd>=10

#####
# 7 #
####Найдите номера моделей и цены всех имеющихся в продаже продуктов (любого типа) производителя B (латинская буква).####

SELECT Product.model, PC.price FROM Product JOIN PC ON Product.model=PC.model AND Product.maker='B'
UNION
SELECT Product.model, Laptop.price FROM Product JOIN Laptop ON Product.model=Laptop.model AND Product.maker='B'
UNION
SELECT Product.model, Printer.price FROM Product JOIN Printer ON Product.model=Printer.model AND Product.maker='B'

#####
# 8 #
####Найдите производителя, выпускающего ПК, но не ПК-блокноты.####

SELECT DISTINCT maker FROM Product WHERE type = 'PC'
EXCEPT
SELECT DISTINCT maker FROM Product WHERE type = 'laptop'

#####
# 9 #
####Найдите производителей ПК с процессором не менее 450 Мгц. Вывести: Maker.####

SELECT DISTINCT maker FROM Product JOIN PC ON Product.model=PC.model WHERE speed>=450

#####
#10 #
####Найдите модели принтеров, имеющих самую высокую цену. Вывести: model, price.####

SELECT model, price FROM Printer WHERE price = (SELECT MAX(price) FROM printer )

#####
#11 #
####Найдите среднюю скорость ПК.####

SELECT AVG (speed) AS speed FROM PC

#####
#12 #
####Найдите среднюю скорость ПК-блокнотов, цена которых превышает 1000 дол.####

SELECT AVG (speed) AS avg_speed FROM Laptop WHERE price>1000

#####
#13 #
####Найдите среднюю скорость ПК, выпущенных производителем A.####

SELECT AVG(speed) AS avg_speed FROM PC JOIN Product ON Product.model=PC.model WHERE Product.maker='A'

#####
#14 #
####Найдите класс, имя и страну для кораблей из таблицы Ships, имеющих не менее 10 орудий.####

SELECT Classes.class, name, country FROM Classes JOIN Ships ON Classes.class=Ships.class WHERE numGuns>=10

#####
#15 #
####Найдите размеры жестких дисков, совпадающих у двух и более PC. Вывести: HD.####

SELECT hd FROM PC GROUP BY hd HAVING COUNT(hd)>=2

#####
#16 #
####Найдите пары моделей PC, имеющих одинаковые скорость и RAM. В результате каждая пара указывается только один раз, т.е. (i,j), но не (j,i).#### 
####Порядок вывода: модель с большим номером, модель с меньшим номером, скорость и RAM.####

SELECT DISTINCT A.model AS model1, B.model AS model2, A.speed, A.ram FROM PC AS A, PC AS B
WHERE A.speed=B.speed AND A.ram=B.ram AND A.model>B.model

#####
#17 #
####Найдите модели ПК-блокнотов, скорость которых меньше скорости каждого из ПК. Вывести: type, model, speed.####

SELECT DISTINCT Product.type, Product.model, Laptop.speed FROM Product JOIN Laptop ON Laptop.speed < (SELECT MIN(speed) FROM PC WHERE Laptop.model = Product.model)
