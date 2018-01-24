# Programacion
Recopilación sobre conceptos 
## Programación Imperativa (Imperative Programming)
Escribir código que describe detalladamente los pasos que el equipo debe realizar para cumplir el objetivo. A veces también se denomina programación algorítmica.
### Programación OOP (Oriented Object Programming)
Programación orientada a objetos. Uso de las clases, herencia polimorfismo y sobrecarga de operadores. 

> En C#, se trata de la metodología básica.
## Programación declarativa (declarative programming)
Crear el problema como un conjunto de funciones que se deben ejecutar. [Diferencias entre la programación funcional y Programación imperativa](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming)
### Programación Funcional (Functional Programming)
Los patrones comprueban que un valor tenga una determinada *forma* y pueden extraer información del valor cuando tienen la forma coincidente ([referencia](https://docs.microsoft.com/es-es/dotnet/csharp/pattern-matching)).
- Evitar los cambios de estado.
  - Estado inmutable:
    - Evita muchos errores ya que **no hay efectos secundarios**.
    - Nos ayuda en sistemas concurrentes o paralelos.
- Funciones puras:
  - No cambia variables o datos de ningún tipo fuera de la función.
  - Es coherente. Con el mismo conjunto de datos de entrada, siempre devolverá el mismo valor de salida.
- Las funciones reciben parámetros y devuelven un resultado (si son funciones puras).
  - El *testing* tiende a ser más sencillo, los resultados son más previsibles.
##### Pipeline
|Imperative 
|---------- 
| Number:0123456789|Number:0123456789
 
````C#
 var sb = new StringBuilder("0123",10); 
 sb.Append(new char[] { '4', '5', '6' });
 sb.AppendFormat("{0}{1}{3}",7,8,9);
 sb.Insert(0,"number: ");
 sb.Replace('n', 'N');
 var str = sb.ToString();
 Console.WriteLine(str); |    xxx
 ````
 | Functional
 |---------- 
 |Number:0123456789
 ````C#
 var str = 
    new StringBuilder("0123",10)
      .Append(new char[] { '4', '5', '6' })
      .AppendFormat("{0}{1}{3}",7,8,9)
      .Insert(0,"number: ")
      .Replace('n', 'N')
      .ToString();
 Console.WriteLine(str);
 ````
 
## Coincidencia de patrones (Pattern Maching)
Los patrones comprueban que un valor tenga una determinada *forma* y pueden extraer información del valor cuando tienen la forma coincidente ([referencia](https://docs.microsoft.com/es-es/dotnet/csharp/pattern-matching)).


`C#`
> `Regex.Match()`

[`C#7`](https://blogs.msdn.microsoft.com/seteplia/2017/10/16/dissecting-the-pattern-matching-in-c-7/)
> operador     `is` y `switch`  

```C#
public static int Count<T>(this IEnumerable<T> e)
{
    switch (e)
    {
        case ICollection<T> c: return c.Count;
        case IReadOnlyCollection<T> c: return c.Count;
        // Matches concurrent collections
        case IProducerConsumerCollection<T> pc: return pc.Count;
        // Matches if e is not null
        case IEnumerable<T> _: return e.Count();
        // Default case is handled when e is null
        default: return 0;
    }
}
```
