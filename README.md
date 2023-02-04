# Dynamic-Power-BI-Financial-Statements
Acted as BI developer for GL retail Corporation to automate and visualize their current reporting whilst improving efficiency and integrity, and developing new insights to provide a competitive urge in the market.  

Task;
> Automate and visual current reporting
> Improve efficiency and reporting integrity
> Develop new insights to provide competitive advantage

GL Retail Corporation
> Retail company with a head office location and 5 retail stores
> Operating successfully for several years
> Data driven approach to turn good performance into great

Below is the final query required to source finance data from the database.
SELECT
FactGLTran
gl.FactGLTranID
gl.GLTranAmount
gl.JournalID
gl.GLTranDescription
gl.GLTranDate
GL Accounts
acc.AlternateKey
GLAcctNum
acc.GLAcctName
acc.Statement
acc.Category
acc.Subcategory
--
Stores
sto.AlternateKey
StoreNum
sto.StoreName
sto.ManagerID
sto.PreviousManagerID
sto.ContactTel
sto.AddressLine1,
sto.AddressLine2,
sto.ZipCode
--
Region
reg.AlternateKey
RegionNum
reg.RegionName
reg.SalesRegionName
--
Last Refresh Date
CONVERT
datetime2 GETDATE at time zone ' at time zone 'Central Standard Time' AS LastRefreshDate
FROM
FactGLTran AS gl
INNER
JOIN dimGLAcct AS acc ON gl.GLAcctID acc.GLAcctID
INNER
JOIN dimStore AS sto ON gl.StoreID sto.StoreID
INNER
JOIN dimRegion AS reg ON sto.RegionID reg.RegionID
