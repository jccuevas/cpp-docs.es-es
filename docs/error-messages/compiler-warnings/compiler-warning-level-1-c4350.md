---
title: Advertencia del compilador (nivel 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 890ecd4fcec1212fa04a58b0eaab8c2eb4206763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187224"
---
# <a name="compiler-warning-level-1-c4350"></a>Advertencia del compilador (nivel 1) C4350

cambio de comportamiento: se llamó a 'miembro1' en lugar de a 'miembro2'

No se puede enlazar un valor r a una referencia no const. En las versiones de C++ visual anteriores a visual Studio 2003, era posible enlazar un valor r a una referencia no const en una inicialización directa. Este código emite ahora una advertencia.

Por compatibilidad con versiones anteriores, todavía es posible enlazar rvalues a referencias no const, pero se prefieren las conversiones estándar siempre que sea posible.

Esta advertencia representa un cambio de comportamiento del compilador de Visual C++ .net 2002. Si está habilitada, es posible que se proporcione esta advertencia para el código correcto. Por ejemplo, se podría proporcionar al usar la plantilla de clase **STD:: auto_ptr** .

Si recibe esta advertencia, examine el código para ver si depende del enlace de rvalues a referencias no const. Agregar un const a la referencia o proporcionar una sobrecarga adicional const-Reference puede resolver el problema.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

En el ejemplo siguiente se genera C4350:

```cpp
// C4350.cpp
// compile with: /W1
#pragma warning (default : 4350)
class A {};

class B
{
public:
   B(B&){}
   // try the following instead:
   // B(const B&){}

   B(A){}
   operator A(){ return A();}
};

B source() { return A(); }

int main()
{
   B ap(source());   // C4350
}
```
