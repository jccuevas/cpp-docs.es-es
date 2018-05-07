---
title: Compilador advertencia (nivel 4) C4471 | Documentos de Microsoft
ms.custom: ''
ms.date: 04/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4471
dev_langs:
- C++
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a530cee3c3fcfec8566d46b116fcc4e71760ed11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4471"></a>Compilador advertencia (nivel 4) C4471
'*enumeración*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se presupone int)  
  
Se encontró una declaración adelantada de una enumeración sin ámbito sin un especificador para el tipo subyacente. De forma predeterminada, Visual C++ supone `int` es el tipo subyacente de una enumeración. Esto puede causar problemas si un tipo diferente se utiliza en la definición de enumeración, por ejemplo, si se especifica un tipo explícito diferente, o si un tipo diferente se establece implícitamente por un inicializador. También puede tener problemas de portabilidad; otros compiladores no supongan `int` es el tipo subyacente de una enumeración.  
  
Esta advertencia está desactivada de forma predeterminada; Puede usar/Wall o /w*N*4471 para habilitarla en la línea de comandos o utilice #pragma [advertencia](../../preprocessor/warning.md) en el archivo de origen.  
  
En algunos casos, esta advertencia es falsa. Si una declaración adelantada de una enumeración aparece después de la definición, se puede activar esta advertencia. Por ejemplo, este código es válido, aunque podría provocar C4471:  
  
```cpp  
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```  
  
## <a name="example"></a>Ejemplo  
En general, resulta seguro utilizar la definición completa para una enumeración sin ámbito en lugar de una declaración adelantada. Puede poner la definición en un archivo de encabezado e incluirlo en archivos de origen que haga referencia a él. Esto funciona en código escrito en C ++ 98 y versiones posteriores. Se recomienda esta solución para portabilidad y la facilidad de mantenimiento.  
  
```cpp  
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```  
  
## <a name="example"></a>Ejemplo  
En C ++ 11, puede agregar un tipo explícito para una enumeración sin ámbito y su declaración adelantada. Se recomienda esta solución solo si la lógica de inclusión de encabezado complejos impide el uso de la definición en lugar de una declaración adelantada. Esta solución puede dar lugar a un problema de mantenimiento: si cambia el tipo subyacente que se usa para la definición de enumeración, también debe cambiar todas las declaraciones adelantadas para que coincida con o tal vez tenga errores silenciosos en el código. La declaración adelantada se puede colocar en un archivo de encabezado para minimizar este problema.  
  
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
  
Si especifica un tipo explícito para una enumeración, se recomienda también habilitar la advertencia [C4369](compiler-warning-level-1-C4369.md), que está activado de forma predeterminada. Esto identifica a los casos donde un elemento de enumeración requiere un tipo diferente que el tipo especificado de forma explícita.
  
## <a name="example"></a>Ejemplo  
Puede cambiar el código para utilizar una enumeración con ámbito, una característica nueva en C ++ 11. La definición y código de cliente que utiliza el tipo de enumeración deben cambiarse para utilizar una enumeración con ámbito. Se recomienda que utilizar una enumeración con ámbito, si tiene problemas con la contaminación de espacios de nombres, como los nombres de elementos de la enumeración definida se limita al ámbito de la enumeración. Otra característica de una enumeración con ámbito es que sus miembros no se puede convertir implícitamente a otro tipo entero o de enumeración, que puede ser un origen de los errores sutiles.

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
  
