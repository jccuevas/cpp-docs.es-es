---
title: Error del compilador C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 8ab2e0d152e4c123fa23512bc0111cebd070b3ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200869"
---
# <a name="compiler-error-c3409"></a>Error del compilador C3409

> no se permite un bloque de atributos vacío

## <a name="remarks"></a>Observaciones

El compilador interpreta los corchetes como un bloque de [atributos](../../windows/attributes-alphabetical-reference.md) , pero no se encontró ningún atributo.

El compilador puede generar este error cuando se usan corchetes como parte de la definición de una expresión lambda. Este error se produce cuando el compilador no puede determinar si los corchetes forman parte de la definición de una expresión lambda o de un bloque de atributos. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Si los corchetes forman parte de un bloque de atributos:

   1. Proporcione uno o más atributos en el bloque de atributos.

   1. Quite el bloque de atributos.

1. Si los corchetes forman parte de una expresión lambda, asegúrese de que la expresión lambda sigue las reglas de sintaxis válidas.

   Para obtener más información sobre la sintaxis de expresiones lambda, vea [Sintaxis de expresiones lambda](../../cpp/lambda-expression-syntax.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3409.

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

En el ejemplo siguiente se genera C3409 porque una expresión lambda usa la especificación `mutable`, pero no proporciona una lista de parámetros. El compilador no puede determinar si los corchetes forman parte de la definición de una expresión lambda o de un bloque de atributos.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Consulte también

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Sintaxis de la expresión lambda](../../cpp/lambda-expression-syntax.md)
