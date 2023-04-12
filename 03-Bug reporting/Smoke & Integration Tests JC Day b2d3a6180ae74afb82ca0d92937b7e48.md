# Smoke & Integration Tests JC Day

| Pass/Fail Cat/Dog | Short Name | Description | Test Type | Expectation | CAT Error Message | AdventureWorks2019 Error Line | AdventureWorksDW2019 Error Line |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ✅ 🐱 | [Sales.SalesOrderHeader x dbo.FactInternetSales] | Count of rows | Smoke | SetsMatch |  |  |  |
| ✅ 🐱 | [Sales.CreditCard] | Len of Card Number | Smoke | SetIsEmpty |  |  |  |
| ✅ 🐱 | [Product.Production.SafetyStockLevel] | SafetyStockLevel not 0 or NULL | Smoke | SetIsEmpty |  |  |  |
| ❌ 🐶 | [Product.Production.StandardCost x ListPrice] | StandardCost not greater than ListPrice | Smoke | SetIsEmpty | No row was expected but at least one row exists. | ProductID: 329 |  |
| ❌ 🐶 | [Product.Production.SellStartDate] | SellStartDate not earlier than 01/01/2000 | Smoke | SetIsEmpty | No row was expected but at least one row exists. | ProductID: 952 |  |
| ✅ 🐱 | [Product.TransactionHistory.TransactionType] | TransactionType is in W, S, P | Smoke | SetIsEmpty |  |  |  |
| ❌ 🐶 | [http://production.product.name/ x dbo.DimProduct.EnglishProductName] | Values of Name should equal values of EnglishProductName | Integration | SetsMatch | The first set and the second set are different | Name: Front Brake  | EnglishProductName: Front Brakes |
| ❌ 🐶 | dbo.DimProduct x dbo.FactProductInventory | Every product in dbo.DimProduct should be in dbo.FactProductInventory | Integration | SetsMatch | The first set and the second set are different | ProductKey: 601 | ProductKey: 3 |
| ❌ 🐶 | Sales.SalesOrderHeader x dbo.FactInternetSales | Product amounts should be equal in both tables | Integration | SetsMatch | The first set and the second set are different | Name: AWC Logo Cap | EnglishProductName: AWC Logo Cap |