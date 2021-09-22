### Question 1

a. I think the most likely cause for such a high AOV (Average Order Value) is that there are some high order value orders (think suppliers buying 1000s of sneakers at once) that is dragging up the entire average. I think it would be more appropiate to calculate the mean after ommiting outlier values

b. I think reporting the average order value after removing the top and bottom 5% outlier values would be the most appropiate

c. The mean after removing the top and bottom 5% outlier is $288.53, one that seems much more reasonable and realistic.

### Question 2

a.

    SELECT 
        Shippers.ShipperName,
        COUNT('ShipID') AS 'value_occurrence'
        
    FROM [Orders]
    JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID

    WHERE Shippers.ShipperName = 'Speedy Express'

    GROUP BY 
    Shippers.ShipperName

    ORDER BY 
    Shippers.ShipperName ASC;

    Output:
    ShipperName     value_occurrence
    Speedy Express	54  

Speedy Expressed shipped 54 orders

b.

    SELECT 
        Employees.LastName,
        COUNT('EmployeeID') AS 'Orders'
        
    FROM [Orders]
    JOIN Employees ON Employees.EmployeeID = Orders.EmployeeID

    GROUP BY 
    Employees.LastName

    ORDER BY 
    Orders DESC
    
    Limit 1;

    Return

    Output:
    LastName    Orders
    Peacock     40

Last name of the employee with the most orders is Peacock with 40 orders

c.

    SELECT 
        Products.ProductName,
        SUM(Quantity) AS Quantity
        
    FROM OrderDetails
    JOIN Orders ON OrderDetails.OrderID = Orders.OrderID
    JOIN Customers ON Orders.CustomerID = Customers.CustomerID
    JOIN Products ON OrderDetails.ProductID = Products.ProductID

    WHERE Customers.Country = 'Germany'

    GROUP BY
        OrderDetails.ProductID
        
    ORDER BY
        Quantity DESC
        
    LIMIT 1;

    Output
    ProductName         Quantity
    Boston Crab Meat    160

Boston Crab Meat is the most popular for those in Germany with 160 ordered









