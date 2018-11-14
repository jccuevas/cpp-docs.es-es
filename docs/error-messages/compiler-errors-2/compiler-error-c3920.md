---
title: Error del compilador C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: d7163cf07a440a0afd1216b3e5cf665326ffb963
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522108"
---
# <a name="compiler-error-c3920"></a>Error del compilador C3920

' operator'': no se puede definir un operador CLR llamada postfijo o el incremento y decremento WinRT operador WinRT o CLR llamará el prefijo correspondiente WinRT o CLR operador (op_Increment/op_Decrement), pero con semántica de postfijo.

Windows Runtime y CLR no admiten el operador de postfijo y no se permiten los operadores de postfijo definidos por el usuario.  Puede definir un operador de prefijo que se usará para ambas operaciones de incremento previo y posterior.

El ejemplo siguiente genera el error C3920 y muestra cómo corregirlo:

```
// C3920.cpp
// compile with: /clr /LD
public value struct V {
   static V operator ++(V me, int)
   // try the following line instead
   // static V operator ++(V me)
   {   // C3920
      me.m_i++;
      return me;
   }

   int m_i;
};
```