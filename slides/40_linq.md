### LINQ (1/3)

##### Language Integrated Query

- Comes in 2 flavors:
  * query syntax (think SQL-like syntax)
    + all operations not supported (e.g. Average, Sum, etc.)
    + so there's still a need to somehow understand method syntax
  * method syntax (think lambdas, arrow functions)

===

### LINQ (2/3)

##### Getting the sum of an array (imperative)

```cs
var weights = new int[] {30, 25, 15, 50, 88, 100, 130};
var total = 0;

for (var i = 0; i < weights.Length; i++)
{
    total += weights[i];
}

Console.WriteLine(total);
```

```bash
> dotnet run
438
```

===

### LINQ (3/3)

##### Getting the sum of an array (declarative)

```cs
var weights = new int[] {30, 25, 15, 50, 88, 100, 130};
Console.WriteLine(weights.Sum());
```

```bash
> dotnet run
438
```