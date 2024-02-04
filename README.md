# UBS-SQL-Schema-Design-
Product Dissection and analysis of core business services and features, with the understanding of features crafted a schema design that reflects the platform's data structure. Created an illustrative Entity-Relationship (ER) diagram, that  vividly depict the entities, attributes, and relationships present within in schema design. The ER diagram will serve as a visual representation of the insights.


 ![image](https://github.com/RohitJaiswal01/UBS-SQL-Schema-Design-/assets/152694882/c72c24d7-91f3-4905-b747-84398d35a12b)

# Product Dissection of UBS

# Company Overview:

UBS works with individuals, families, institutions, and corporations around the world to help answer some of life's questions – whether through award winning wealth management advisory, investment banking and asset management expertise, or private and corporate banking services in Switzerland*. In June 2023, Credit Suisse became a UBS Group company. With a large and diverse team operating internationally, UBS has a presence in all major financial centers in more than 50 countries. 
UBS provides wealth management, asset management, and investment banking services for private, corporate, and institutional clients with international service. UBS manages the largest amount of private wealth in the world, counting approximately half of The World’s Billionaire among its clients. UBS also maintains a global investment bank and is considered a primary market maker. 


# Top Facilities and Services of UBS:

### Wealth Management 
UBS has been helping wealthy individuals and families pursue what matters most to them has been the purpose for over 160 years. Wealth management is a comprehensive financial advisory service that involves the coordination of various financial activities to help individuals and families manage, grow, and preserve their wealth. The wealth management services include but not limited to services such as:
Risk Management
Risk management helps to identify, assess, and mitigate potential risks associated with your financial portfolio. It consists of giving a thorough analysis of the financial situation to identify various types of risks. Evaluate risk tolerance, financial goals, and time horizon to tailor a risk management strategy that aligns with the client's unique circumstances.


### Insurance Planning
Insurance planning of the HNIs and families is the subdivision of the wealth management that evaluates and provides recommendations on the appropriate mix of insurance products to address identified risks, insurance coverage including life, health, property, and liability insurance. Integrate insurance products as a crucial component to wealth management strategy to safeguard client assets. 


### Tax Planning
Tax planning with respect to wealth management refers to optimizing the financial strategy by minimizing tax liabilities and maximizing after-tax returns for the clients, including comprehensive analysis of the financial situation to identify potential tax implications and areas for tax optimization and the placement of assets across various account types (taxable, tax-deferred, and tax-free) to enhance tax efficiency etc.


### Asset Management 
Asset Management services of UBS plays a role to help strategically manage and grow the investments to achieve client’s financial goals. Being a part of the wealth management services the access to investment capabilities and investment styles of asset management division has extended its client base to individuals, institutes and corporations. Utilizing a range of asset classes, including equities, fixed income, alternatives, and cash, to build a well-balanced and diversified investment portfolio. Leveraging UBS's research capabilities and expertise to make informed investment decisions. Offering sustainable and responsible investment options such as environmental, social, and governance (ESG) factors into the investment process when constructing portfolios.


### Investment Banking
Investment Banking Provide strategic advisory services for mergers and acquisitions (M&A), facilitate capital raising activities through public offerings (IPOs). It provides international perspectives and access to a broad range of capital markets. Offer insights and strategies based on a deep understanding of market dynamics in various industries. Assist clients in optimizing their capital structure and financing through capital raising and debt to enhance shareholder value. With the help of the investment banking division UBS can enhance its customer base and services by combining the asset management clients and giving all round support to the clients on both sides.
### Corporate Banking
Business checking and savings accounts with upgradable features to meet the unique needs of businesses. Comprehensive commercial lending solutions, including term loans and lines of credit. Cutting-edge digital banking platforms for corporate clients, facilitating efficient financial management and reporting. 
Personal Banking
Everyday banking services, including savings and checking accounts, debit cards, and online/mobile banking, loans and financing etc. Exclusive banking services for high-net-worth individuals, including personalized financial solutions and access to a dedicated team of wealth management professionals. 

## Entities:
### Client
ClientID (Primary Key): Unique identifier for each client.
FirstName: First name of the client.
LastName: Last name of the client.
Address: Address of the client.
ContactDetails: Contact details of the client.
AccountType: Type of account (e.g., individual, corporate).

### Personal Banking
PersonalBankingID (Primary Key): Unique identifier for each personal banking account.
ClientID (Foreign Key): References the Client table, linking to the corresponding client.
AccountNumber: Account number for the personal banking account.
Balance: Current balance in the personal banking account.
CreditScore: Credit score associated with the client.

### Corporate Banking
CorporateBankingID (Primary Key): Unique identifier for each corporate banking account.
ClientID (Foreign Key): References the Client table, linking to the corresponding client.
CompanyName: Name of the corporate entity.
Industry: Industry to which the corporate client belongs.
Revenue: Revenue generated by the corporate client.

### Wealth Management 
WMID (Primary Key): Unique identifier for each wealth management account.
ClientID (Foreign Key): References the Client table, linking to the corresponding client.
PortfolioValue: Value of the client's investment portfolio.
RiskAppetite: Client's risk tolerance.
FinancialGoals: Goals related to financial planning.
InvestmentHorizon: Duration over which the client plans to invest.
AdvisoryTeam: Team providing advisory services.

### Risk Management
RiskID (Primary Key): Unique identifier for each risk management entry.
WMID (Foreign Key): References the WealthManagement table, linking to the corresponding wealth management account.
RiskType: Type of risk being managed.
RiskLevel: Level or severity of the identified risk.

### Insurance Planning
InsuranceID (Primary Key): Unique identifier for each insurance planning entry.
WMID (Foreign Key): References the WealthManagement table, linking to the corresponding wealth management account.
InsuranceType: Type of insurance being planned.
CoverageAmount: Amount of coverage planned for the insurance.

### Tax Planning
TaxID (Primary Key): Unique identifier for each tax planning entry.
WMID (Foreign Key): References the WealthManagement table, linking to the corresponding wealth management account.
TaxStrategy: Strategy for tax planning.
TaxAdvisors: Advisors involved in tax planning.


### Asset Management
AMID (Primary Key): Unique identifier for each asset management account.
ClientID (Foreign Key): References the Client table, linking to the corresponding client.
InvestmentPortfolio: Description of the client's investment portfolio.
FundPerformance: Performance details of investment funds.
AssetAllocation: Allocation of assets in the investment portfolio
AssetManager_id: This is the bank integral asset manager id each manager can manage many client assets at a time.

### Investment Banking
IBID (Primary Key): Unique identifier for each investment banking account.
ClientID (Foreign Key): References the Client table, linking to the corresponding client.
IPOsManaged: Number of Initial Public Offerings managed by the investment banking division.
MAndATransactions: Number of mergers and acquisitions transactions managed.
CapitalRaising: Amount of capital raised
AssetManager_id: This is the bank integral asset manager id that buys or sells assets through the bank's investment banking division.

### Investment
InvestmentID (Primary Key): Unique identifier for each investment.
ClientID (Foreign Key): References the Client table, linking to the corresponding client.
WMID (Foreign Key): References the WealthManagement table, linking to the corresponding wealth management account.
AMID (Foreign Key): References the AssetManagement table, linking to the corresponding asset management account.
IBID (Foreign Key): References the InvestmentBanking table, linking to the corresponding investment banking account.
InvestmentType: Type of investment.
InvestmentAmount: Amount invested.
Date: Date of the investment.

## Relationships:
### Client - Personal Banking (1: Many):
One client can have multiple personal banking accounts like saving, current or fixed.

PersonalBanking references Client using ClientID as a foreign key.

### Client - Corporate Banking (1: Many):
One client can have multiple corporate banking accounts.

CorporateBanking references Client using ClientID as a foreign key.

### Client - Wealth Management (1:1):
One client can have one wealth management account.

WealthManagement references Client using ClientID as a foreign key.

### Wealth Management - Risk Management (1: Many):
One wealth management account can have multiple risk management entries.

RiskManagement references WealthManagement using WMID as a foreign key.

### Wealth Management - Insurance Planning (1: Many):
One wealth management account can have multiple insurance planning entries.

InsurancePlanning references WealthManagement using WMID as a foreign key.

### Wealth Management - Tax Planning (1: Many):
One wealth management account can have multiple tax planning entries.

TaxPlanning references WealthManagement using WMID as a foreign key.

### Client - Asset Management (1: Many):
One client can have multiple asset management accounts.

AssetManagement references Client using ClientID as a foreign key.

### Client - Investment Banking (1: 1):
One client can have one investment banking account.
InvestmentBanking references Client using ClientID as a foreign key.

### Wealth Management - Investment (1: Many):
One wealth management account can have multiple investments.

Investment references WealthManagement using WMID as a foreign key.

### Asset Management - Investment (1: Many):
One asset management account can have multiple investments.

Investment references AssetManagement using AMID as a foreign key.

### Investment Banking - Investment (1: Many):
One investment banking account can have multiple investments.

Investment references InvestmentBanking using IBID as a foreign key.



# ER Diagram: 
Let’s construct an ER diagram for schema design of UBS with our approach, this would be an estimated schema model for UBS that highlights relationships and attributes of the entities. This would be showing the major features or facilities being provided by UBS to its clients. The core business divisions and sub divisions have been shown in the diagram along with the relationships between them determining the data flows and giving an understanding of the data architecture framework of the UBS.

![image](https://github.com/RohitJaiswal01/UBS-SQL-Schema-Design-/assets/152694882/2e94a1c9-1598-475b-9ae0-b67bf835e740)

# Conclusion:
In this case study we delved into UBS and analysed its core business and services being provided by the bank, that solves the financial problems faced by various clients ranging from HNIs, Corporations, institutions etc.  UBS has been a well-established financial service provider in the domain of wealth management, asset management, investment banking and personal and corporate banking.
We have made an estimated Entity – Relationship diagram, making the business divisions of the company as entities and relationships as the way data is segregated and managed. It has provided understanding of the data model design on how the data can be stored and the relationships between the business division and sub division can be formulated, in order to manage and solve complex data related requirements. 

