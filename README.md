# PowerApps: Different-ways-to-use-Patch-function
<br><br><br>

# 1. Create A New Record With Power Apps Patch Function

### Syntax
Patch(Datasource, BaseRecord, NewRecord)
<br><br>
### Input
Countries Table in SharePoint



| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |

<br><br>
### Code

```
Patch(
    Countries,
    Defaults(Countries),
    {
        'Country Name': "USA",
        Capital: "Washington, D.C.",
        Population: "400.9 mil"
    }
)
```
<br><br><br>

# 2. Update An Existing Record Using Power Apps Patch Function

### Syntax
Patch(Datasource, BaseRecord, ChangeRecord)
<br><br>
### Input
Countries Table in SharePoint




| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | 400.10 mil     |

<br><br>
### Code

```
Patch(
    Countries,
    LookUp(
        Countries,
        ID = 5
    ),
    {
        Population: "334.9 mil"
    }
)
```
### Output
Countries Table in SharePoint
| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | ***334.9 mil***   |

<br><br><br>

# 3. Get The Result Of The Patch Function

### Syntax
Set(VariableName, Patch(Datasource, BaseRecord, ChangeRecord))
<br><br>
### Input
Countries Table in SharePoint




| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | 334.9 mil     |

<br><br>
### Code

```
Set(
    VarCountryDetail,
    Patch(
        Countries,
        Defaults(Countries),
        {
            'Country Name': "France",
            Capital: "Paris",
            Population: "68.17 mil"
        }
    )
)
```
### Output
Countries Table in SharePoint
| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | 334.9 mil   |
| ***6***    | ***France***     | ***Paris***     | ***68.17 mil***   |
<br>
varCountryDetail record in Power Apps

```
{
    ID: 6,
    CountryName: "France",
    Capital: "Paris",
    Population: "68.17 mil",
    Craeted: Date(2024, 11,27),
    Modified: Date(2024, 11, 27)
}
```
<br><br><br>

# 4.Create Multiple New Records With Power Apps Patch Function

### Syntax
Patch(Datasource, NewRecordsCollection)
<br><br>
### Input
Countries Table in SharePoint




| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | 334.9 mil     |
| 6    | France     | Paris     | 68.17 mil   |

<br><br>
### Code

```
ClearCollect(
    colCountries,
    {
        CountryName: "Italy",
        Capital: "Rome",
        Population: "58.76"
    },
    {
        CountryName: "Japan",
        Capital: "Tokyo",
        Population: "124.5"
    },
    {
        CountryName: "Germany",
        Capital: "Berlin",
        Population: "84.48"
    }
);
Patch(
    Countries,
    ShowColumns(
        colCountries,
        CountryName,
        Capital,
        Population
    )
)
```
### Output
Countries Table in SharePoint
| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | 334.9 mil   |
| 6    | France     | Paris     | 68.17 mil   |
| ***7***    | ***Italy***     | ***Rome***     | ***58.76 mil***   |
| ***8***    | ***Japan***     | ***Tokyo***     | ***124.5 mil***   |
| ***9***    | ***Germany***     | ***Berlin***     | ***84.48 mil***   |


<br><br><br>

# 5.Edit Multiple Existing Records Using Power Apps Patch Function

### Syntax
Patch(Datasource, NewRecordsCollection)
<br><br>
### Input
Countries Table in SharePoint




| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | 334.9 mil     |
| 6    | France     | Paris     | 68.17 mil   |
| 7    | Italy     | Rome     | 58.76 mil   |
| 8    | Japan     | Tokyo     | 124.5 mil   |
| 9    | Germany     | Berlin     | 84.48 mil   |

<br><br>
### Code

```
ClearCollect(
    colCountries,
    {
        ID: 6,
        Population: "1 mil"
    },
    {
        ID: 7,
        Population: "1 mil"
    },
    {
        ID: 8,
        Population: "1 mil"
    }
);
Patch(
    Countries,
    ShowColumns(
        colCountries,
        ID,
        Population
    )
)
```
### Output
Countries Table in SharePoint
| ID | Country Name | Capital | Population |
|----------|----------|----------|----------|
| 1    | United Kingdom     | London     | 68.3 mil     |
| 2    | Australia     | Canberra     | 26.64 mil     |
| 3    | New Zealand     | Wellington     | 5.22 mil     |
| 4    | Canada     | Ottawa     | 40.1 mil     |
| 5    | USA     | Washington, D.C.     | 334.9 mil   |
| 6    | France     | Paris     | 68.17 mil   |
| 7    | Italy     | Rome     | ***1 mil***   |
| 8    | Japan     | Tokyo     | ***1 mil***   |
| 9    | Germany     | Berlin     | ***1 mil***   |
