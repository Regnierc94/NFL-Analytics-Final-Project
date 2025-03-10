# NFL-Analytics
A data set revolving around passing yards
import requests
import pandas as pd
from bs4 import BeautifulSoup
url = "https://www.pro-football-reference.com/years/2023/passing.htm"
tables = pd.read_html(url)


for i, table in enumerate(tables):
    print(f"Table {i}:\n", table.head(), "\n")

\
top_5_qb = tables[0]

#uploading sport reference data with header and dataset
top_5_qb.columns = top_5_qb.iloc[0]  
top_5_qb = top_5_qb[1:]  

#index confirmation
top_5_qb = top_5_qb.reset_index(drop=True)

#column list
print("Updated Column Names:", top_5_qb.columns.tolist())

# Account for criteria
top_5_qb = top_5_qb.rename(columns={
    top_5_qb.columns[0]: "Player",
    top_5_qb.columns[1]: "Team",
    top_5_qb.columns[7]: "Pass Yards",
    top_5_qb.columns[8]: "TD",
    top_5_qb.columns[9]: "INT",
    top_5_qb.columns[10]: "Comp %",
    top_5_qb.columns[12]: "Y/A",
    top_5_qb.columns[14]: "Passer Rating"
})
top_5_qb_filtered.to_csv("qb_stats_2023.csv", index=False)
top_5_qb_filtered
