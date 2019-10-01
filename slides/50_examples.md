##### Cool 😎 idea 💡 for our debt tracking startup

<img alt="debt" src="images/utang.jpg" style="width: 600px; height; 400px" />

===

### Debt class

```cs
class Debt
{
    public string Debtor { get; set; }
    public int Amount { get; set; }
    public DateTime WhenBorrowed { get; set; }

    public Debt(string debtor, int amount, DateTime whenBorrowed)
    {
        Debtor = debtor;
        Amount = amount;
        WhenBorrowed = whenBorrowed;
    }
}
```

===

### Some debts

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

### Get total owed to rich kid
##### Step 1: get an array of debt amounts

```cs
var amounts = from debt in debts
              select debt.Amount;
Console.WriteLine(amounts.ToJson());
```

```json
[                    
  60,                
  2500,              
  430,               
  290,               
  500,               
  1000,              
  800                
]                    
```

===

### Get total owed to rich kid
##### Step 2: get the sum of the array

You already know how to do this

```cs
var amounts = from debt in debts
              select debt.Amount;
Console.WriteLine("Total owed: " + amounts.Sum());
```

```bash
Total owed: 5580               
```

===

### Get the average amount owed by each person?

===

### Get the average amount owed by each person?
##### Step 2: get the sum of the array

You already know how to do this

```cs
var amounts = from debt in debts
              select debt.Amount;
Console.WriteLine("Total owed: " + amounts.Average());
```

```bash
Total owed: 797.142857142857
```
