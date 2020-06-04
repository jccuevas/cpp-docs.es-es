---
title: Advertencia del compilador (nivel 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 47e278bbc69b972f6acc391d6b3278ab8d159c08
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990704"
---
# <a name="compiler-warning-level-4-c4516"></a>Advertencia del compilador (nivel 4) C4516

' Class:: Symbol ': las declaraciones de acceso están desusadas; las declaraciones Using de miembro proporcionan una mejor alternativa

El Comité C++ ANSI ha declarado declaraciones de acceso (cambiando el acceso de un miembro en una clase derivada sin la palabra clave [using](../../cpp/using-declaration.md) ) para que estén obsoletas. Es posible que las declaraciones de acceso no se admitan C++en versiones futuras de.

En el ejemplo siguiente se genera C4516:

```cpp
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```
