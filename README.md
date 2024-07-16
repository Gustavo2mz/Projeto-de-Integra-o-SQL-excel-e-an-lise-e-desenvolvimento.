# Projeto-de-Integra-o-SQL-excel-e-an-lise-e-desenvolvimento.
'''
CREATE OR ALTER VIEW VENDAS AS
SELECT
    f.SalesOrderNumber AS 'Numero do Pedido',
    f.OrderDate AS 'Data do Pedido',
    pc.EnglishProductCategoryName AS 'Categoria ',
    c.FirstName + ' ' + c.LastName AS 'Nome do Cliente',
    c.Gender AS 'Sexo',
    st.SalesTerritoryCountry 'País',
    f.OrderQuantity 'Quantidade Vendida',
    f.TotalProductCost AS 'Custo Total do Produto',
    f.SalesAmount AS 'Receita da Venda'
FROM
    FactInternetSales AS f
JOIN
    DimCustomer AS c ON f.CustomerKey = c.CustomerKey
JOIN
    DimSalesTerritory AS st ON f.SalesTerritoryKey = st.SalesTerritoryKey
JOIN
    DimProduct AS p ON f.ProductKey = p.ProductKey
JOIN
    DimProductSubcategory AS ps ON p.ProductSubcategoryKey = ps.ProductSubcategoryKey
JOIN
    DimProductCategory AS pc ON ps.ProductCategoryKey = pc.ProductCategoryKey;
  
