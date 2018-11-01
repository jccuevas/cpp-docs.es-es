---
title: Error del compilador C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: 4a54a9c629a1abaa4f1c5d15d06448e82cf25561
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538860"
---
# <a name="compiler-error-c3195"></a>Error del compilador C3195

'operador' : está reservado y no se puede utilizar como miembro de una clase ref o de un tipo de valor. Los operadores CLR o WinRT se deben definir mediante la palabra clave 'operator'

El compilador detectó una definición de operador con la sintaxis de Extensiones administradas para C++. Debe usar la sintaxis de C++ para los operadores.

El ejemplo siguiente genera el error C3195 y muestra cómo corregirlo:

```
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```