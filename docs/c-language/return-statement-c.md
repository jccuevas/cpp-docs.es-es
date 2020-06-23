---
title: return (Instrucción) (C)
description: La instrucción "return" del lenguaje C termina la ejecución de la función y, opcionalmente, devuelve un valor al autor de la llamada.
ms.date: 06/10/2020
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: 7d518aa17185c96de15c8f9aa9b65ae5c72bd014
ms.sourcegitcommit: 01b911613606c3fc92cbd9ca48cca6046a7e8258
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716299"
---
# <a name="return-statement-c"></a>return (Instrucción) (C)

Una instrucción **`return`** termina la ejecución de una función y devuelve el control a la función de llamada. La ejecución se reanuda en la función de llamada, en el punto que sigue inmediatamente a la llamada. Una instrucción **`return`** puede devolver un valor a la función de llamada. Para obtener más información, consulte [Tipo de valor devuelto](../c-language/return-type.md).

## <a name="syntax"></a>Sintaxis

> *jump-statement*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`return`** *expression*&#8203;<sub>opt</sub> **`;`**

El valor de *expression*, si existe, se devuelve a la función que llama. Si *expression* se omite, el valor devuelto de la función es indefinido. El valor de expression, si está presente, se evalúa y después se convierte al tipo devuelto por la función. Cuando una instrucción **`return`** contiene una expresión en funciones que tiene un tipo de valor devuelto **`void`** , el compilador genera una advertencia y la expresión no se evalúa.

Si no aparece ninguna instrucción **`return`** en una definición de función, el control vuelve automáticamente a la función de llamada después de que se ejecute la última instrucción de la función llamada. En este caso, el valor devuelto de la función llamada es indefinido. Si la función tiene un tipo de valor devuelto distinto de **`void`** , se trata de un error grave, y el compilador imprime un mensaje de diagnóstico de advertencia. Si la función tiene un tipo de valor devuelto **`void`** , este comportamiento es correcto, pero puede que se considere de un estilo insuficiente. Use una instrucción **`return`** sin formato para que su intención sea clara.

En ingeniería, se recomienda siempre especificar un tipo de valor devuelto para las funciones. Si no se necesita ningún valor devuelto, declare la función para que tenga el tipo de valor devuelto **`void`** . Si no se especifica ningún tipo de valor devuelto, el compilador de C supone un tipo de valor devuelto predeterminado de **`int`** .

Muchos programadores usan paréntesis para incluir el argumento *expression* de la instrucción **`return`** . Sin embargo, C no necesita los paréntesis.

El compilador puede emitir un mensaje de diagnóstico de advertencia sobre código inaccesible si encuentra instrucciones situadas después de la instrucción **`return`** .

En una función **`main`** , la instrucción **`return`** y la expresión son opcionales. Lo que sucede con el valor devuelto, si se especifica uno, depende de la implementación. **Específico de Microsoft**: La implementación de Microsoft C devuelve el valor de la expresión al proceso que invocó el programa, como *`cmd.exe`* . Si no se proporciona ninguna expresión **`return`** , el tiempo de ejecución de Microsoft C devuelve un valor que indica "correcto" (0) o "incorrecto" (un valor distinto de cero).

## <a name="example"></a>Ejemplo

Este ejemplo es un programa en varias partes. Muestra la instrucción **`return`** y cómo se usa para terminar la ejecución de la función y, opcionalmente, para devolver un valor.

```C
// C_return_statement.c
// Compile using: cl /W4 C_return_statement.c
#include <limits.h>      // for INT_MAX
#include <stdio.h>       // for printf

long long square( int value )
{
    // Cast one operand to long long to force the
    // expression to be evaluated as type long long.
    // Note that parentheses around the return expression
    // are allowed, but not required here.
    return ( value * (long long) value );
}
```

La función `square` devuelve el cuadrado de su argumento, en un tipo más amplio para evitar un error aritmético. **Específico de Microsoft**: En la implementación de Microsoft C, el tipo **`long long`** es lo suficientemente grande como para contener el producto de dos valores de **`int`** sin desbordamiento.

Los paréntesis que rodean la expresión **`return`** en `square` se evalúan como parte de la expresión y no son necesarios para la instrucción **`return`** .

```C
double ratio( int numerator, int denominator )
{
    // Cast one operand to double to force floating-point
    // division. Otherwise, integer division is used,
    // then the result is converted to the return type.
    return numerator / (double) denominator;
}
```

La función `ratio` devuelve la relación de sus dos argumentos **`int`** como un valor de **`double`** de punto flotante. La expresión **`return`** se ve forzada a usar una operación de punto flotante mediante la conversión de uno de los operandos a **`double`** . De lo contrario, se utilizaría el operador de división de enteros y se perdería la parte fraccionaria.

```C
void report_square( void )
{
    int value = INT_MAX;
    long long squared = 0LL;
    squared = square( value );
    printf( "value = %d, squared = %lld\n", value, squared );
    return; // Use an empty expression to return void.
}
```

La función `report_square` llama a `square` con un valor de parámetro de `INT_MAX`, el valor entero con signo más grande que cabe en **`int`** . El resultado de **`long long`** se almacena en `squared` y se imprime. La función `report_square` tiene un tipo de valor devuelto **`void`** , por lo que no tiene ninguna expresión en su instrucción **`return`** .

```C
void report_ratio( int top, int bottom )
{
    double fraction = ratio( top, bottom );
    printf( "%d / %d = %.16f\n", top, bottom, fraction );
    // It's okay to have no return statement for functions
    // that have void return types.
}
```

La función `report_ratio` llama a `ratio` con valores de parámetro de `1` y `INT_MAX`. El resultado de **`double`** se almacena en `fraction` y se imprime. La función `report_ratio` tiene un tipo de valor devuelto **`void`** , por lo que no es necesario devolver explícitamente un valor. La ejecución de `report_ratio` "cae fuera de la parte inferior" y no devuelve ningún valor al autor de la llamada.

```C
int main()
{
    int n = 1;
    int x = INT_MAX;

    report_square();
    report_ratio( n, x );

    return 0;
}
```

La función **`main`** llama a dos funciones: `report_square` y `report_ratio`. Como `report_square` no toma ningún parámetro y devuelve **`void`** , no se asigna el resultado a una variable. Del mismo modo, `report_ratio` devuelve **`void`** , por lo que tampoco se guarda el valor devuelto. Después de cada una de estas llamadas a funciones, la ejecución continúa en la instrucción siguiente. A continuación, **`main`** devuelve un valor de `0` (que se suele usar para informar de un proceso correcto) para terminar el programa.

Para compilar el ejemplo, cree un archivo de código fuente denominado *`C_return_statement.c`* . A continuación, copie todo el código de ejemplo en el orden que se muestra. Guarde el archivo y compílelo en una ventana del símbolo del sistema para desarrolladores mediante el comando:

**`cl /W4 C_return_statement.c`**

A continuación, para ejecutar el código de ejemplo, escriba **`C_return_statement.exe`** en el símbolo del sistema. El resultado del ejemplo es similar a lo siguiente:

```Output
value = 2147483647, squared = 4611686014132420609
1 / 2147483647 = 0.0000000004656613
```

## <a name="see-also"></a>Vea también

[Instrucciones](../c-language/statements-c.md)
