# Data engineer challenge

Congratulations and thanks for applying.

We designed a simple data engineering problem so you can display all your skills. All the information needed to solve the challenge is displayed below.
	
# Delivery Instructions

Your code must be delivered in a **private** Github repository. Once you are done, you must give permission to the user [rafalee](https://github.com/rafalee) and send an email with the repository’s link to the same email address that last contacted you. 

Your repository must have a README file with sufficient instructions on how to run your solution and the automated tests.

## What we would like to see in your solution:
- Python >= 3
- Well written tests with good coverage (> 70%)
- Dockerized solution

# The Challenge

Our research team would like to run some analysis on brazilian hedge funds. In order to do so, they need easy access to the funds historical data. Your goal is to create a simple process that will fetch, organize and persist that data. Once that data is stored, you must make the data available to the research team.

## You application must have have the functionalities below:

- ETL process that will fetch hedge fund daily data from CVM and persist it (more about the data source will be discussed later)

- You should store the daily return of the fund (ret), that is calculated as:
  - ret(t) = (VL_QUOTA(t) / VL_QUOTA(t - 1)) - 1

- Ways for other users to query and access that data. The data series should be returned sorted by date containing all fields (including the daily return field).
  - The query must accept the following parameters:
    - CNPJ: Mandatory parameter
      - The data retrieved will belong to that CNPJ, use the field CNPJ_FUNDO from the source csv file
    - Start Date: Optional parameter
      - Filter the data for dates greater than or equal than Start Date, use the field DT_COMPTC from the source csv file
    - End Date: Optional parameter
      - Filter the data for dates lesser than End Date, use the field DT_COMPTC from the source csv file
      
# About the data source
All the data is freely available on the CVM website at “Portal Dados Abertos CVM” (http://dados.cvm.gov.br/). You will find all the links to the files you need in the link below:

[http://dados.cvm.gov.br/dados/FI/DOC/INF_DIARIO/DADOS/](http://dados.cvm.gov.br/dados/FI/DOC/INF_DIARIO/DADOS/)

For this challenge, you will only need to get data from 2017 untill today. Each file contains one month of data, denoted by the file name in the following format: `inf_diario_fi_{YYYY}{MM}.csv` (e.g..: `inf_diario_fi_201701.csv` for january 2017).

The files are in CSV format containing the following fields:
- **CNPJ_FUNDO**: this is the unique identifier of a hedge fund
- **DT_COMPTC**: date of record
- **VL_TOTAL**: Total value of portfolio (BRL)
- **VL_QUOTA**: Quota value
- **VL_PATRIM_LIQ**: Fund net worth (BRL)
- **CAPTC_DIA**: Total investments of the day (BRL)
- **RESG_DIA**: Total withdrawals of the day (BRL)
- **NR_COTST**: Total number of investors


# FAQ

- Are there any particular frameworks, databases systems or tools I should use for this challenge?
  - No, use what you feel most comfortable with and that will showcase your data engineering and coding skills. The only technical requirement for this challenge is that you must use Python on the development process.
  
- The challenge asks for a good test coverage of the code, do I need to follow TDD?
  - Not necessarily. The most important thing is that your code must have good tests and test cases, this part is just as important as the code itself.

- Should I include a database dump file with the data in my repository?
  - No, your database content should be created by running your ETL process.
