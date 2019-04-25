---
title: Error del compilador C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 24f107e0c1f74f95afc521c8a4c888a26a35c13a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173397"
---
# <a name="compiler-error-c3409"></a>Error del compilador C3409

> no se permite el bloque de atributos vacío

## <a name="remarks"></a>Comentarios

Los corchetes se interpretaron en el compilador como un [atributo](../../windows/attributes-alphabetical-reference.md) bloque, pero no hay atributos que se han encontrado.

El compilador puede generar este error cuando utilice corchetes como parte de la definición de una expresión lambda. Este error se produce cuando el compilador no puede determinar si los corchetes son parte de la definición de una expresión lambda o de un bloque de atributos. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Si los corchetes forman parte de un bloque de atributos:

   1. Proporcionar uno o varios atributos en el bloque de atributos.

   1. Quite el bloque de atributos.

1. Si los corchetes forman parte de una expresión lambda, asegúrese de que la expresión lambda sigue las reglas de sintaxis válida.

   Para obtener más información sobre la sintaxis de expresiones lambda, vea [sintaxis de expresión Lambda](../../cpp/lambda-expression-syntax.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3409.

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente genera el error C3409 porque una expresión lambda usa la `mutable` especificación, pero no proporciona una lista de parámetros. El compilador no puede determinar si los corchetes son parte de la definición de una expresión lambda o de un bloque de atributos.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Vea también

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Sintaxis de la expresión lambda](../../cpp/lambda-expression-syntax.md)