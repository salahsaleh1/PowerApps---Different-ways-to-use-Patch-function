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
