##### Debt data are scattered (Group per person)

```cs
var details = from debt in debts
              where debt.Debtor == "Judas" || debt.Debtor == "Arms"
              group debt by debt.Debtor into debtsPerPerson
              select debtsPerPerson;
              
Console.WriteLine(details.ToJson());
```

```json
[                                          
  [ 
    { "Debtor": "Arms", "Amount": 2500, "WhenBorrowed": "2019-07-15T00:00:00" }, 
    { "Debtor": "Arms", "Amount": 1000, "WhenBorrowed": "2018-10-02T00:00:00" }                            
  ],                                       
  [ { "Debtor": "Judas", "Amount": 1000, "WhenBorrowed": "2017-12-31T00:00:00" }, 
    { "Debtor": "Judas", "Amount": 50, "WhenBorrowed": "2017-09-14T00:00:00" }, 
    { "Debtor": "Judas", "Amount": 50, "WhenBorrowed": "2019-07-02T00:00:00"}                              
  ]                                        
]                                          
```

===

### Amount Owed Per Person

```cs
var closeFriends = new string[] { "Judas" ,"Arms", "Seth", "Ariessa" };
var details = from debt in debts
              where closeFriends.Contains(debt.Debtor)
              group debt by debt.Debtor into debtor
              select new {
                  Debtor = debtor.Key,
                  TotalOwed = debtor.Sum(debt => debt.Amount)
              };
              
Console.WriteLine(details.ToJson());
```

```json
[ { "Debtor": "Ariessa", "TotalOwed": 60 },                         
  { "Debtor": "Arms", "TotalOwed": 3500 },                         
  { "Debtor": "Seth", "TotalOwed": 1090 },                         
  { "Debtor": "Judas", "TotalOwed": 1100 } ]                            
```

===

##### Debtors Sorted Alphabetically

```cs
var closeFriends = new string[] { "Judas" ,"Arms", "Seth", "Ariessa" };
var details = from debt in debts
              where closeFriends.Contains(debt.Debtor)
              group debt by debt.Debtor into debtor
              select new {
                  Debtor = debtor.Key,
                  TotalOwed = debtor.Sum(debt => debt.Amount)
              };
var sorted = from debt in details
             orderby debt.Debtor
             select debt;

Console.WriteLine(sorted.ToJson());
```

```json
[ { "Debtor": "Ariessa", "TotalOwed": 60 },                         
  { "Debtor": "Arms", "TotalOwed": 3500 },
  { "Debtor": "Judas", "TotalOwed": 1100 },                     
  { "Debtor": "Seth", "TotalOwed": 1090 } ]                            
```

===

##### Debtors Sorted by Total Amount Owed

```cs
var closeFriends = new string[] { "Judas" ,"Arms", "Seth", "Ariessa" };
var details = from debt in debts
              where closeFriends.Contains(debt.Debtor)
              group debt by debt.Debtor into debtor
              select new {
                  Debtor = debtor.Key,
                  TotalOwed = debtor.Sum(debt => debt.Amount)
              };
var sorted = from debt in details
             orderby debt.TotalOwed descending
             select debt;

Console.WriteLine(sorted.ToJson());
```

```json
[ { "Debtor": "Arms", "TotalOwed": 3500 },
  { "Debtor": "Judas", "TotalOwed": 1100 },                     
  { "Debtor": "Seth", "TotalOwed": 1090 },
  { "Debtor": "Ariessa", "TotalOwed": 60 } ]                            
```
