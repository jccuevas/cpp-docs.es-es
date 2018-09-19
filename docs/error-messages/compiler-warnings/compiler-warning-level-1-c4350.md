---
title: Compilador advertencia (nivel 1) C4350 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad49a7471be257fa0c22f66fa1bb2bbea049194
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096696"
---
# <a name="compiler-warning-level-1-c4350"></a>Advertencia del compilador (nivel 1) C4350

cambio de comportamiento: se llamó a 'miembro1' en lugar de a 'miembro2'

No se puede enlazar un valor r a una referencia no constante. En versiones de Visual C++ antes de Visual Studio 2003, era posible enlazar un valor r a una referencia distinta de const en una inicialización directa. Este código ahora emite una advertencia.

Por compatibilidad con versiones anteriores, es posible enlazar valores r a referencias no const, pero se prefieren las conversiones estándar siempre que sea posible.

Esta advertencia representa un cambio de comportamiento del compilador de Visual C++ .NET 2002. Si está habilitada, esta advertencia puede haberse dado para código correcto. Por ejemplo, podría darse al utilizar el **std:: auto_ptr** plantilla de clase.

Si aparece esta advertencia, examine el código para ver si depende de enlace rvalues a referencias no constante. Agregando una constante a la referencia o proporcionar una sobrecarga de referencia const adicional para solucionar el problema.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

El ejemplo siguiente genera C4350:

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