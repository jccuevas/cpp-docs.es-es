---
title: Error del compilador C3409 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 338a98adb45ee9fc8eb392853a5693d10a171940
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058840"
---
# <a name="compiler-error-c3409"></a>Error del compilador C3409

no se permite el bloque de atributos vacío

Los corchetes se interpretaron en el compilador como un [atributo](../../windows/cpp-attributes-reference.md) bloque, pero no hay atributos que se han encontrado.

El compilador puede generar este error cuando utilice corchetes como parte de la definición de una expresión lambda. Este error se produce cuando el compilador no puede determinar si los corchetes son parte de la definición de una expresión lambda o de un bloque de atributos. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Si los corchetes forman parte de un bloque de atributos:

   1. Proporcionar uno o varios atributos en el bloque de atributos.

   1. Quite el bloque de atributos.

1. Si los corchetes forman parte de una expresión lambda:

   1. Asegúrese de que la expresión lambda sigue las reglas de sintaxis válida.

         Para obtener más información sobre la sintaxis de expresiones lambda, vea [sintaxis de expresión Lambda](../../cpp/lambda-expression-syntax.md).

    2.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3409.

```
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

```
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Vea también

[attribute](../../windows/cpp-attributes-reference.md)<br/>
[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Sintaxis de la expresión lambda](../../cpp/lambda-expression-syntax.md)