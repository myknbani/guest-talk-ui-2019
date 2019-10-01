Searching
=========

### Again, the debts

```cs
var debts = new Debt[]
{
    new Debt("Ariessa", 60, new DateTime(2019, 4, 1)),
    new Debt("Arms", 2500, new DateTime(2019, 7, 15)),
    new Debt("Psalm", 430, new DateTime(2019, 8, 31)),
    new Debt("Seth", 290, new DateTime(2017, 5, 22)),
    new Debt("Rave", 500, new DateTime(2018, 9, 30)),
    new Debt("Arms", 1000, new DateTime(2018, 10, 2)),
    new Debt("Seth", 800, new DateTime(2015, 12, 25))
};
```

===

### Does Arms owe me anything?

===

### Does Arms owe me anything?

```cs
var armsDebts = from debt in debts
                where debt.Debtor == "SeTh"
                select debt; // the entire Debt object
Console.WriteLine(armsDebts.ToJson());
```

```json
[
  {
    "Debtor": "Arms",
    "Amount": 2500,
    "WhenBorrowed": "2019-07-15T00:00:00"
  },
  {
    "Debtor": "Arms",
    "Amount": 1000,
    "WhenBorrowed": "2018-10-02T00:00:00"
  }
]             
```

===

### Search for a debtor case-insensitively

===

### Search for a debtor case-insensitively

```cs
var sethDebts = from debt in debts
                where debt.Debtor.ToLower() == "SeTh".ToLower()
                select debt; // the entire Debt object
Console.WriteLine(sethDebts.ToJson());
```

```json
[
  {
    "Debtor": "Seth",
    "Amount": 290,
    "WhenBorrowed": "2017-05-22T00:00:00"
  },
  {
    "Debtor": "Seth",
    "Amount": 800,
    "WhenBorrowed": "2015-12-25T00:00:00"
  }
]          
```

===

Huge debts (500 pesos or more)

===

Huge debts (500 pesos or more)

```cs
var bigAmounts = from debt in debts
                 where debt.Amount >= 500

                 // select some fields
                 select new { debt.Debtor, debt.Amount };
Console.WriteLine(bigAmounts.ToJson());
```

```json
[
  { "Debtor": "Arms", "Amount": 2500 },
  { "Debtor": "Rave", "Amount": 500 },
  { "Debtor": "Arms", "Amount": 1000 },
  { "Debtor": "Seth", "Amount": 800 }
]                                      
```

===

### Get the debts owed by either Psalm or Ariessa

===

### Get the debts owed by either Psalm or Ariessa

```cs
var boracayTrippers = new string[]{ "Psalm", "Ariessa" };
var shamelessDebtors = from debt in debts
                       where boracayTrippers.Contains(debt.Debtor)
                       select new { debt.Debtor, debt.Amount };

Console.WriteLine(shamelessDebtors.ToJson());
```

```json
[
  { "Debtor": "Ariessa", "Amount": 60 },
  { "Debtor": "Psalm", "Amount": 430 }
]
```
