---
title: ADVERTENCIA del compilador (nivel 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 5d7ed7dc84c0ef61c7789deeb128b99977fa6028
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076933"
---
# <a name="compiler-warning-level-4-c4471"></a>ADVERTENCIA del compilador (nivel 4) C4471

'*enumeración*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se supone int)

Se encontró una declaración adelantada de una enumeración sin ámbito sin un especificador para el tipo subyacente. De forma predeterminada, C++ Visual supone `int` es el tipo subyacente de una enumeración. Esto puede producir problemas si se usa un tipo diferente en la definición de la enumeración, por ejemplo, si se especifica un tipo explícito diferente, o si un inicializador establece implícitamente un tipo diferente. También puede tener problemas de portabilidad; otros compiladores no suponen `int` es el tipo subyacente de una enumeración.

Esta advertencia está desactivada de forma predeterminada; puede usar/Wall o/w*N*4471 para habilitarla en la línea de comandos o usar #pragma [ADVERTENCIA](../../preprocessor/warning.md) en el archivo de código fuente.

En algunos casos, esta advertencia es falsa. Si una declaración adelantada de una enumeración aparece después de la definición, esta advertencia se puede activar. Por ejemplo, este código es válido, aunque puede producir C4471:

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>Ejemplo

En general, es seguro usar la definición completa para una enumeración sin ámbito en lugar de una declaración adelantada. Puede colocar la definición en un archivo de encabezado e incluirla en los archivos de código fuente que hacen referencia a ella. Esto funciona en el código escrito para C++ 98 y versiones posteriores. Se recomienda esta solución para la portabilidad y la facilidad de mantenimiento.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>Ejemplo

En C++ 11, puede Agregar un tipo explícito a una enumeración sin ámbito y a su declaración adelantada. Se recomienda esta solución solo si la lógica de inclusión de encabezados complejos impide el uso de la definición en lugar de una declaración adelantada. Esta solución puede dar lugar a un problema de mantenimiento: Si cambia el tipo subyacente que se usa para la definición de la enumeración, también debe cambiar todas las declaraciones adelantadas para que coincidan, o puede que haya errores silenciosos en el código. Puede colocar la declaración adelantada en un archivo de encabezado para minimizar este problema.

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

Si especifica un tipo explícito para una enumeración, se recomienda habilitar también [C4369](compiler-warning-level-1-C4369.md)de advertencia, que está activada de forma predeterminada. Esto identifica los casos en los que un elemento de enumeración requiere un tipo diferente del tipo especificado explícitamente.

## <a name="example"></a>Ejemplo

Puede cambiar el código para usar una enumeración con ámbito, una característica que es nueva en C++ 11. Tanto la definición como cualquier código de cliente que use el tipo de enumeración deben cambiarse para usar una enumeración con ámbito. Se recomienda usar una enumeración con ámbito si tiene problemas con la contaminación del espacio de nombres, ya que los nombres de los elementos de enumeración definidos se limitan al ámbito de la enumeración. Otra característica de una enumeración con ámbito es que sus miembros no se pueden convertir implícitamente a otro tipo entero o de enumeración, que puede ser una fuente de errores sutiles.

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```
