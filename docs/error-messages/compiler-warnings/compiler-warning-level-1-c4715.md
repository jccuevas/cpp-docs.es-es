---
title: Advertencia del compilador (nivel 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 7dba86d591f18fd7c9c562078204916000d47384
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175329"
---
# <a name="compiler-warning-level-1-c4715"></a>Advertencia del compilador (nivel 1) C4715

' función ': no todas las rutas de acceso de control devuelven un valor

La función especificada no puede devolver un valor.

## <a name="example"></a>Ejemplo

```cpp
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Para evitar esta advertencia, modifique el código para que todas las rutas de acceso asignen un valor devuelto a la función:

```cpp
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Es posible que el código contenga una llamada a una función que no devuelve nunca, como en el ejemplo siguiente:

```cpp
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

Este código también genera una advertencia, ya que el compilador no sabe que `fatal` nunca devuelve. Para evitar que este código genere un mensaje de error, declare `fatal` mediante [__declspec (noreturn)](../../cpp/noreturn.md).
