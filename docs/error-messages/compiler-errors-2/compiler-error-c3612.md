---
title: Error del compilador C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: ab18381d3f263e3207662e1667ac5c835983412f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344485"
---
# <a name="compiler-error-c3612"></a>Error del compilador C3612

'type': una clase sellada no puede ser abstracta

Tipos definidos mediante `value` son sealed de forma predeterminada, y una clase es abstracta, a menos que lo implementa todos los métodos de su base. Una clase abstracta sellada no puede ser una clase base ni se puede crear instancias.

Para obtener más información, consulte [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3612:

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```