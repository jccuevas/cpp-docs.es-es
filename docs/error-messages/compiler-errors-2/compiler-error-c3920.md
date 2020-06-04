---
title: Error del compilador C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: 416752054f7397a058329e1ee4bdaef693dd0d28
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758468"
---
# <a name="compiler-error-c3920"></a>Error del compilador C3920

' Operator ' ': no se puede definir un operador de WinRT o CLR de incremento o decremento postfijo que llame al operador de winrt o CLR de postfijo que llamará al operador WinRT o CLR de prefijo correspondiente (op_Increment/op_Decrement), pero con semántica de postfijo

Windows Runtime y CLR no admiten el operador de postfijo y no se permiten los operadores de postfijo definidos por el usuario.  Puede definir un operador de prefijo que se usará para ambas operaciones de incremento previo y posterior.

El ejemplo siguiente genera el error C3920 y muestra cómo corregirlo:

```cpp
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
