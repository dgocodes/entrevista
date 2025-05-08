# Métodos úteis em C#

## 📐 Math (System.Math)

- `Math.Abs(x)` — valor absoluto  
- `Math.Ceiling(x)` — arredonda para cima  
- `Math.Floor(x)` — arredonda para baixo  
- `Math.Round(x)` — arredonda normalmente  
- `Math.Truncate(x)` — remove parte decimal  
- `Math.Sqrt(x)` — raiz quadrada  
- `Math.Pow(x, y)` — potência  
- `Math.Log(x)` — logaritmo natural  
- `Math.Log10(x)` — logaritmo base 10  
- `Math.Exp(x)` — exponencial (e^x)  
- `Math.Max(a, b)` / `Math.Min(a, b)`  
- `Math.Clamp(valor, min, max)`  
- `Math.PI` / `Math.E`  

---

## 🎲 Random (System.Random)

```csharp
var rand = new Random();
```

- `rand.Next()` — int ≥ 0  
- `rand.Next(max)` — int entre 0 e max-1  
- `rand.Next(min, max)` — int entre min e max-1  
- `rand.NextDouble()` — double entre 0.0 e 1.0  
- `rand.NextBytes(byte[])`  

---

## 🔁 LINQ (System.Linq)

```csharp
using System.Linq;
```

### Filtragem
- `Where()`  
- `Select()`  
- `Distinct()`  
- `OfType<T>()`  

### Ordenação
- `OrderBy()`  
- `OrderByDescending()`  
- `ThenBy()`  
- `Reverse()`  

### Agregação
- `Count()`, `Sum()`, `Min()`, `Max()`, `Average()`  

### Elementos
- `First()`, `FirstOrDefault()`  
- `Last()`, `Single()`  
- `ElementAt()`  

### Comparações
- `Any()`, `All()`, `Contains()`  

### Conversões
- `ToList()`, `ToArray()`, `ToDictionary()`, `ToHashSet()`  

---

## 🔤 Strings (System.String)

- `string.Length`  
- `string.ToLower()`, `ToUpper()`  
- `string.Contains("abc")`  
- `string.StartsWith("a")`, `EndsWith("z")`  
- `string.IndexOf("texto")`  
- `string.Substring(start, length)`  
- `string.Replace("a", "b")`  
- `string.Trim()`, `TrimStart()`, `TrimEnd()`  
- `string.Split(',')`  
- `string.Join(",", array)`  

---

## 🧱 Arrays / List<T>

### Arrays
- `array.Length`  
- `Array.IndexOf(array, value)`  
- `Array.Reverse(array)`  
- `Array.Sort(array)`  

### List<T>
```csharp
var lista = new List<string>();
```

- `lista.Add()`  
- `lista.Remove()`  
- `lista.Contains()`  
- `lista.Count`  
- `lista.Clear()`  
- `lista.IndexOf(item)`  
- `lista.Sort()`, `lista.Reverse()`