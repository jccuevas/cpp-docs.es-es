---
title: Literales numéricos, booleanos yC++de puntero ()
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: 467300501ffbbf8063e203d4c7395af34a954ed0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301371"
---
# <a name="numeric-boolean-and-pointer-literals"></a>Literales numéricos, booleanos y de puntero

Un literal es un elemento de programa que representa directamente un valor. En este artículo se tratan los literales de tipo entero, de punto flotante, booleanos y de puntero. Para obtener información sobre los literales de cadena y carácter, vea [literales deC++cadena y carácter ()](../cpp/string-and-character-literals-cpp.md). También puede definir sus propios literales basados en cualquiera de estas categorías; para obtener más información [, vea literales definidos porC++el usuario ()](../cpp/user-defined-literals-cpp.md) .

. Puede usar literales en muchos contextos, pero lo más común es utilizarlos para inicializar variables con nombre y pasar argumentos a funciones:

```cpp
const int answer = 42; // integer literal
double d = sin(108.87);     //floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

A veces es importante indicar al compilador cómo interpretar un literal o qué tipo específico debe darle. Esto se logra anexando prefijos o sufijos al literal. Por ejemplo, el prefijo 0x indica al compilador que interprete el número que sigue como un valor hexadecimal, por ejemplo 0x35. El sufijo completa indica al compilador que trate el valor como un tipo Long **Long sin signo** , como en 5894345ULL. Consulte las siguientes secciones para obtener una lista completa de los prefijos y sufijos para cada tipo de literal.

## <a name="integer-literals"></a>Literales enteros

Los literales enteros comienzan con un dígito y no tienen partes fraccionarias ni exponentes. Se pueden especificar en formato decimal, octal o hexadecimal. Pueden especificar tipos con signo o sin signo y tipos largos o cortos.

Si no existe ningún prefijo o sufijo, el compilador proporcionará un tipo de valor literal entero **int** (32 bits), si el valor se ajusta, de lo contrario, lo dará a un tipo Long **Long** (64 bits).

Para especificar un literal entero decimal, comience la especificación por un dígito distinto de cero. Por ejemplo:

```cpp
int i = 157;   // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
int
```

Para especificar un literal entero octal, comience la especificación por 0, seguido de una secuencia de dígitos entre 0 y 7. Los dígitos 8 y 9 se consideran errores al especificar un literal octal. Por ejemplo:

```cpp
int i = 0377;   // Octal literal
int j = 0397;        // Error: 9 is not an octal digit
```

Para especificar un literal entero hexadecimal, inicie la especificación con `0x` o `0X` (no importa si la “x” está en mayúsculas o minúsculas), seguido de una secuencia de dígitos entre `0` y `9` y de `a` (o `A`) a `f` (o `F`). Los dígitos hexadecimales de `a` (o `A`) a `f` (o `F`) representan valores comprendidos en el intervalo de 10 a 15. Por ejemplo:

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;        // Equal to i
```

Para especificar un tipo sin signo, use el sufijo `u` o `U`. Para especificar un tipo Long, use el sufijo `l` o `L`. Para especificar un tipo entero de 64 bits, utilice el sufijo LL o ll. El sufijo i64 sigue siendo compatible, pero debe evitarse porque es específico de Microsoft y no es portátil. Por ejemplo:

```cpp
unsigned val_1 = 328u;             // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**Separadores de dígitos**: puede usar el carácter de comilla simple (apóstrofo) para separar los valores de ubicación en números mayores con el fin de facilitar la lectura de los usuarios. Los separadores no afectan a la compilación.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>Literales de punto flotante

Los literales de punto flotante especifican los valores que debe tener una parte fraccionaria. Estos valores contienen separadores decimales ( **.** ) y pueden contener exponentes.

Los literales de punto flotante tienen una “mantisa” que especifica el valor del número, un “exponente” que especifica la magnitud del número y un sufijo opcional que especifica el tipo de literal. La mantisa se especifica como una secuencia de dígitos seguidos de un punto y de una secuencia opcional de dígitos que representan la parte fraccionaria del número. Por ejemplo:

```cpp
18.46
38.
```

El exponente, si está presente, especifica la magnitud del número como potencia de 10, tal como se muestra en el ejemplo siguiente:

```cpp
18.46e0      // 18.46
18.46e1           // 184.6
```

El exponente se puede especificar utilizando `e` o `E`, que tienen el mismo significado, seguido de un signo opcional (+ o-) y una secuencia de dígitos.  Si un exponente está presente, el separador decimal final es innecesario en los números enteros como `18E0`.

Los literales de punto flotante tienen el tipo **Double**de forma predeterminada. Mediante el uso de los sufijos `f` o `l` (o `F` o `L`, el sufijo no distingue entre mayúsculas y minúsculas), el literal se puede especificar como **float** o **Long Double**, respectivamente.

Aunque **Long Double** y **Double** tienen la misma representación, no son del mismo tipo. Por ejemplo, puede haber funciones sobrecargadas como

```cpp
void func( double );
```

y

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Literales booleanos

Los literales booleanos son **true** y **false**.

## <a name="pointer-literal-c11"></a>Literal de puntero (C++11)

C++introduce el literal [nullptr](../cpp/nullptr.md) para especificar un puntero inicializado en cero. En el código portable, se debe usar **nullptr** en lugar de cero de tipo entero o macros como null.

## <a name="binary-literals-c14"></a>Literales binarios (C++14)

Un literal binario puede especificarse mediante el uso del prefijo `0B` o `0b` seguido por una secuencia de unos y ceros:

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>Evite usar literales como “constantes mágicas”

Puede usar literales directamente en expresiones e instrucciones, aunque no siempre es una buena práctica de programación:

```cpp
if (num < 100)
    return "Success";
```

En el ejemplo anterior podría ser mejor usar una constante con nombre que tenga un significado claro, como, por ejemplo, “MAXIMUM_ERROR_THRESHOLD”. Y si los usuarios finales ven el valor devuelto “Correcto”, sería mejor usar una constante de cadena con nombre que se pueda almacenar en una sola ubicación en un archivo desde el que se pueda localizar a otros idiomas. Además, usar constantes con nombre ayuda a comprender el objetivo del código a otras personas y a usted mismo.

## <a name="see-also"></a>Vea también

[Convenciones léxicas](../cpp/lexical-conventions.md)<br/>
[C++Literales de cadena](../cpp/string-and-character-literals-cpp.md)<br/>
[C++Literales definidos por el usuario](../cpp/user-defined-literals-cpp.md)