### Bad News (1/3)

- I don't hate loops
- Loops - basic element of any programming language
- Non-trivial programs will have loops
  * written directly
  * indirectly (through abstractions) 

Consider this line without loops

```cs
Console.WriteLine("michael".ToUpper());
```

===

### Bad News (2/3)

```cs
static class Screamer
{
    public static string BeAngry(this string normal)
    {
        var result = "";
        for (var i = 0; i < normal.Length; i++)
        {
            if (normal[i] >= 97 && normal[i] <= 122)
            {
                result += (char) (normal[i] - 32);
            }
            else
            {
                result += normal[i];
            }
        }
        return result + "!!!";
    }
}
```

===

### Bad News (3/3)

Our own version of `ToUpper()`, powered by loops!
```cs
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("michael".BeAngry());
    }
}
```

The output:
```bash
> dotnet run
MICHAEL!!!
```