---
title: Advertencia del compilador (nivel 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221038"
---
# <a name="compiler-warning-level-4-c4516"></a>Advertencia del compilador (nivel 4) C4516

'clase:: símbolo': las declaraciones de acceso están desusadas; declaraciones using de miembros son una alternativa mejor

El Comité de ANSI C++ ha declarado las declaraciones de acceso (cambiar el acceso de un miembro en una clase derivada sin la [mediante](../../cpp/using-declaration.md) palabra clave) a estar obsoletas. Las declaraciones de acceso no pueden admitir futuras versiones de C++.

El ejemplo siguiente genera C4516:

```
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