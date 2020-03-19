---
title: Funciones intrínsecas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
ms.openlocfilehash: a7203f65ae3c4ba3bfd19e2f1c2013386c1e34c9
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467130"
---
# <a name="intrinsic-functions"></a>Funciones intrínsecas

Una expresión en SAL puede ser una expresión CC++ o siempre que se trata de una expresión que no tiene efectos secundarios; por ejemplo, + +,--, y las llamadas a función tienen efectos secundarios en este contexto.  Sin embargo, SAL proporciona algunos objetos similares a funciones y algunos símbolos reservados que se pueden usar en las expresiones SAL. Estas se conocen como *funciones intrínsecas*.

## <a name="general-purpose"></a>Uso general

Las siguientes anotaciones de la función intrínsecas proporcionan una utilidad general para SAL.

|Anotación|Descripción|
|----------------|-----------------|
|`_Curr_`|Sinónimo del objeto que se está anotando actualmente.  Cuando se utiliza la anotación `_At_`, `_Curr_` es igual que el primer parámetro que se va a `_At_`.  De lo contrario, es el parámetro o el valor completo de la función o devolución con el que está asociada léxicamente la anotación.|
|`_Inexpressible_(expr)`|Expresa una situación en la que el tamaño de un búfer es demasiado complejo para representarlo mediante una expresión de anotación; por ejemplo, cuando se calcula examinando un conjunto de datos de entrada y contando a continuación los miembros seleccionados.|
|`_Nullterm_length_(param)`|`param` es el número de elementos en el búfer hasta, pero sin incluir un terminador null. Se puede aplicar a cualquier búfer de tipo no agregado, no void.|
|`_Old_(expr)`|Cuando se evalúa en condición previa, `_Old_` devuelve el valor de entrada `expr`.  Cuando se evalúa en una condición posterior, devuelve el valor `expr` tal y como se habría evaluado en condición previa.|
|`_Param_(n)`|El parámetro `n`TH para una función, contando entre 1 y `n`, y `n` es una constante entera literal. Si el parámetro se denomina, esta anotación es idéntica a tener acceso al parámetro por su nombre. **Nota:** `n` puede hacer referencia a los parámetros posicionales definidos por puntos suspensivos o que se pueden usar en prototipos de función donde no se usan nombres.|
|`return`|La palabra claveC++ C/reserved `return` se puede usar en una expresión sal para indicar el valor devuelto de una función.  El valor solo está disponible en post State; se trata de un error de sintaxis para usarlo en el estado anterior.|

## <a name="string-specific"></a>Específico de cadena

Las siguientes anotaciones de función intrínseca permiten la manipulación de cadenas. Las cuatro funciones tienen el mismo propósito: devolver el número de elementos del tipo que se encuentra antes de un terminador nulo. Las diferencias son los tipos de datos de los elementos a los que se hace referencia. Tenga en cuenta que si desea especificar la longitud de un búfer terminado en null que no está compuesto por caracteres, use la anotación `_Nullterm_length_(param)` de la sección anterior.

|Anotación|Descripción|
|----------------|-----------------|
|`_String_length_(param)`|`param` es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación está reservada para tipos de cadena de caracteres.|
|`strlen(param)`|`param` es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación se reserva para su uso en matrices de caracteres y se parece a la función en tiempo de ejecución de C [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param` es el número de elementos de la cadena hasta un terminador null (pero sin incluirlo). Esta anotación se reserva para su uso en matrices de caracteres anchos y se parece a la función de tiempo de ejecución de C [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Consulte también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)
