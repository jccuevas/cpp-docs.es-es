---
title: Compilador advertencia (nivel 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 0345b730b8fc37329f632bb5d8486c67efd8e3b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400791"
---
# <a name="compiler-warning-level-4-c4471"></a>Compilador advertencia (nivel 4) C4471

'*enumeración*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se presupone int)

Se encontró una declaración adelantada de una enumeración sin ámbito sin un especificador para el tipo subyacente. De forma predeterminada, Visual C++ supone `int` es el tipo subyacente para una enumeración. Esto puede causar problemas si un tipo diferente se usa en la definición de enumeración, por ejemplo, si se especifica un tipo explícito diferente, o si se establece implícitamente un tipo diferente por un inicializador. También puede tener problemas de portabilidad; otros compiladores no suponen `int` es el tipo subyacente de una enumeración.

Esta advertencia está desactivada de forma predeterminada; Puede usar/Wall o /w*N*4471 para habilitarla en la línea de comandos, o utilice #pragma [advertencia](../../preprocessor/warning.md) en el archivo de origen.

En algunos casos, esta advertencia es falsa. Si una declaración adelantada de una enumeración aparece después de la definición, se puede desencadenar esta advertencia. Por ejemplo, este código es válido, aunque puede producir C4471:

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>Ejemplo

En general, es seguro que se usará la definición completa para una enumeración sin ámbito, en lugar de una declaración adelantada. Puede incluir la definición de un archivo de encabezado e inclúyalo en archivos de origen que haga referencia a él. Esto funciona en código escrito para C ++ 98 y versiones posteriores. Se recomienda esta solución para la portabilidad y facilidad de mantenimiento.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>Ejemplo

En C ++ 11, puede agregar un tipo explícito para una enumeración sin ámbito y su declaración adelantada. Se recomienda esta solución solo si la lógica de inclusión de encabezado complejos impide el uso de la definición en lugar de una declaración adelantada. Esta solución puede dar lugar a un problema de mantenimiento: si cambia el tipo subyacente que se usa para la definición de enumeración, también debe cambiar todas las declaraciones adelantadas para que coincida con o puede surgir errores silenciosos en el código. La declaración adelantada puede colocar en un archivo de encabezado para minimizar este problema.

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

Si especifica un tipo explícito para una enumeración, se recomienda también habilitar la advertencia [C4369](compiler-warning-level-1-C4369.md), que está activada de forma predeterminada. Esto identifica a los casos donde un elemento de enumeración requiere un tipo diferente que el tipo especificado de forma explícita.

## <a name="example"></a>Ejemplo

Puede cambiar el código para utilizar una enumeración con ámbito, una característica nueva en C ++ 11. La definición y cualquier código de cliente que usa el tipo de enumeración deben cambiarse para utilizar una enumeración con ámbito. Se recomienda que utilizar una enumeración con ámbito si tiene problemas con la contaminación de espacios de nombres, como los nombres de elementos de la enumeración definida se limitan al ámbito de la enumeración. Otra característica de una enumeración con ámbito es que sus miembros no pueden convertirse implícitamente a otro tipo entero o de enumeración, que puede ser una fuente de errores sutiles.

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

