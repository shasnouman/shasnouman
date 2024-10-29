---open the compiler
---Load the data
---Run the code
---Interpret the results

CREATE TABLE ecommercedataset (
    OrderID INT primary key,
    CustomerID varchar(100),
    OrderDate date,
    ProductID varchar(100),
    ProductCategory varchar(100),
    Quantity INT,
    Price INT,
    TotalAmount INT,
    CustomerLocation varchar(100)
);

LOAD DATA LOCAL INFILE 'ecommercedataset.CSV'
INTO TABLE ecommercedataset
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;


SELECT *
FROM `ecommercedataset`
WHERE OrderDate IS NULL 
   OR Quantity IS NULL 
   OR TotalAmount IS NULL 
   OR Price IS NULL;


SELECT *
FROM `ecommercedataset`  
WHERE OrderDate > CURRENT_DATE;


SELECT *
FROM `ecommercedataset`  
WHERE Quantity < 0 OR Quantity > 100;


SELECT *
FROM `ecommercedataset`
WHERE TotalAmount <> (Quantity * Price);
