---
title: Compilador advertencia (nivel 1) C4715 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4715
dev_langs:
- C++
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3de829992bfa650280768a2fcd761feaeaece0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061375"
---
# <a name="compiler-warning-level-1-c4715"></a>Advertencia del compilador (nivel 1) C4715

'function': no todas las rutas de acceso de control devuelven un valor

La función especificada puede que no puede devolver un valor.

## <a name="example"></a>Ejemplo

```
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Para evitar esta advertencia, modifique el código para que todas las rutas de asignación un valor devuelto a la función:

```
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Es posible que el código puede contener una llamada a una función que nunca devuelve resultados, como se muestra en el ejemplo siguiente:

```
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

Este código también genera una advertencia, ya que el compilador no sabe que `fatal` no devuelve nunca. Para evitar que este código genera un mensaje de error, declare `fatal` mediante [__declspec (noreturn)](../../cpp/noreturn.md).