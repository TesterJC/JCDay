# Adventure Works Cycles - Production

## CAT tests

We're working with the AdventureWorks2019 and AdventureWorksDW2019 databases, which collect data about a fictional multinational bicycle manufacturer called Adventure Works Cycles, and with the Power BI report DQaaS Lab, which is used by the CEO, production department head, and development team.

Data needs to be checked because important business decisions are made based on it. Key stakeholders and production department heads have listed basic requirements for QA that the data must meet.

Section A lists requirements for Smoke tests, and Section B lists requirements for integration tests for tables in the AdventureWorks2019 database and tables in the AdventureWorksDW2019 database.

At the end of the document, you can find information about tables in AdventureWorks2019.

<br>

## A)  Smoke tests

| Test requirement | Table name in AdventureWorks2019 database | Query |
| --- | --- | --- |
| Values in the SafetyStockLevel column must not contain 0 or NULL | [Production].[Product] | |
| The value in the StandardCost column must not be greater than the value in the ListPrice column | [Production].[Product] | |
| The date in the SellStartDate column must not be earlier than 1/1/2000 (that means 31/12/1999, 30/12/1999 etc) |[Production].[Product]| |
| The value in the TransactionType column must contain only the values W, S, or P |[Production].[TransactionHistory] | |

<br>

## B)  Integration tests

| Test requirement | Table name in AdventureWorks2019 | Table name in AdventureWorksDW2019 | Query AdventureWorks2019 | Query AdventureWorksDW2019 |
| --- | --- | --- | --- | --- |
| Values of Name in the Product table must be the same as in the DimProduct table | [Production].[Product] | [dbo].[DimProduct] |  |  |
| Every product in the DimProduct table must have a record in the FactProductInventory table | - | 1. [dbo].[DimProduct], <br> 2. [dbo].[FactProductInventory] | - |  |
| The total amount for each product in the SalesOrderHeader table must be equal to the total amount in the FactInternetSales table | [Sales].[SalesOrderHeader] | [dbo].[FactInternetSales] | | |

<br>

### Overview of tables for the Production department in the AdventureWorks2019 database

  |Table name | Brief description |
  |---|---|
  |Production.Culture                                 |Lookup table containing the languages in which some AdventureWorks data is stored.
  |Production.Document                                |Product maintenance documents.
  |Production.Illustration                            |Bicycle assembly diagrams
  |Production.Product                                 |Products sold or used in the manufacturing of sold products.
  |Production.ProductCategory                         |High-level product categorization.
  |Production.ProductDescription                      |Product descriptions in several languages.
  |Production.ProductDocument                         |Cross-reference table mapping products to related product documents.
  |Production.ProductModel                            |Product model classification.
  |Production.ProductModelIllustration                |Cross-reference table mapping product models and illustrations.
  |Production.ProductModelProductDescriptionCulture   |Cross-reference table mapping product descriptions and the language the description is written in.
  |Production.ProductPhoto                            |Product images.
  |Production.ProductProductPhoto                     |Cross-reference table mapping products and product photos.
  |Production.ProductReview                           |Customer reviews of products they have purchased.
  |Production.ProductSubcategory                      |Product subcategories. See ProductCategory table.
  |Production.UnitMeasure                             |Unit of measure lookup table.

<br>

### Table schema in the AdventureWorks2019 database

![Schema Production tabulek](Images/media/SchemaTabulek.png)
