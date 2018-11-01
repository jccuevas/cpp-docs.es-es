---
title: Advertencia del compilador (nivel 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: f165ea3b54b78e2f8fae995815e309d55101244e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501236"
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