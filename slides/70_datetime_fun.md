### Reminding us of the people we should nag, I remember Judas also owes me some

```cs
var debts = new Debt[]
{
    new Debt("Ariessa", 60, new DateTime(2019, 4, 1)),
    new Debt("Arms", 2500, new DateTime(2019, 7, 15)),
    new Debt("Psalm", 430, new DateTime(2019, 8, 31)),
    new Debt("Seth", 290, new DateTime(2017, 5, 22)),
    new Debt("Rave", 500, new DateTime(2018, 9, 30)),
    new Debt("Arms", 1000, new DateTime(2018, 10, 2)),
    new Debt("Seth", 800, new DateTime(2015, 12, 25)),
    new Debt("Judas", 1000, new DateTime(2017, 12, 31)),
    new Debt("Judas", 50, new DateTime(2017, 9, 14)),
    new Debt("Judas", 50, new DateTime(2019, 7, 2)),
};
```

===

### Get debts more than 2 years old

===

### Get debts more than 2 years old

```cs
var shamelessNonPayers = from debt in debts
                         where debt.WhenBorrowed <= 2.Years().Ago() 
                         select debt;            // ⬆⬆⬆🤯😲🙀😱

// 2.Years().Ago() is powered by the FluentDateTime extension
```

```json
[{
  "Debtor": "Seth", 
  "Amount": 290,                           
  "WhenBorrowed": "2017-05-22T00:00:00"
}, {
  "Debtor": "Seth",                        
  "Amount": 800,                           
  "WhenBorrowed": "2015-12-25T00:00:00"
}, {
  "Debtor": "Judas",                       
  "Amount": 50,                            
  "WhenBorrowed": "2017-09-14T00:00:00"    
}]                                            
```

===

### Recent debts (3 months ago and newer)

===

##### Recent debts (3 months ago and newer)

```cs
var recentDebts = from debt in debts
                  where debt.WhenBorrowed >= 3.Months().Ago()
                  select debt;

Console.WriteLine(recentDebts.ToJson());
```

```json
$ dotnet run
[{
  "Debtor": "Arms",
  "Amount": 2500,
  "WhenBorrowed": "2019-07-15T00:00:00"
},{
  "Debtor": "Psalm",
  "Amount": 430,
  "WhenBorrowed": "2019-08-31T00:00:00"
},{
  "Debtor": "Judas",
  "Amount": 50,
  "WhenBorrowed": "2019-07-02T00:00:00"
}]                                     
```

===

### <span style="text-transform: none">FluentDateTime</span> Demo (1/2)

Code 
```cs
Console.WriteLine("Now: " + DateTime.Now);
Console.WriteLine("3 days ago: " + 3.Days().Ago());
Console.WriteLine("3 months ago: " + 3.Months().Ago());
Console.WriteLine("3 weeks ago: " + 3.Weeks().Ago());
Console.WriteLine("3 years ago: " + 3.Years().Ago());
```

Output
```bash
Now: 10/1/2019 12:55:22 PM
3 days ago: 9/28/2019 12:55:22 PM
3 months ago: 7/1/2019 12:55:22 PM
3 weeks ago: 9/10/2019 12:55:22 PM
3 years ago: 10/1/2016 12:55:22 PM
```

===

### <span style="text-transform: none">FluentDateTime</span> Demo (2/2)

Code
```cs
Console.WriteLine("Now: " + DateTime.Now);
Console.WriteLine("7 days from now: " + (DateTime.Now + 7.Days()));
Console.WriteLine("Reservation expiry in 2 weeks: " + 2.Weeks().FromNow());
Console.WriteLine("6 months and 1 day ago: " + (DateTime.Now - 6.Months() - 1.Days()));
Console.WriteLine("6 months and 1 day ago: " + (DateTime.Now - 181.Days()));
```

Output
```bash
Now: 10/1/2019 12:55:22 PM
7 days from now: 10/8/2019 2:40:28 PM
Reservation expiry in 2 weeks: 10/15/2019 12:55:22 PM
6 months and 1 day ago: 4/3/2019 12:55:22 PM
6 months and 1 day ago: 4/3/2019 12:55:22 PM
```
