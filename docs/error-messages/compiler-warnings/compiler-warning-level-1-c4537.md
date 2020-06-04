---
title: Advertencia del compilador (nivel 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 81058f153228d3d8fbf4097c140962d0cb9677e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186366"
---
# <a name="compiler-warning-level-1-c4537"></a>Advertencia del compilador (nivel 1) C4537

> '*objeto*': '*operador*' aplicado a un tipo no UDT

## <a name="remarks"></a>Observaciones

Se pasó una referencia en la que se esperaba un objeto (tipo definido por el usuario). Una referencia no es un objeto, pero el código ensamblador alineado no puede realizar la distinción. El compilador genera código como si el *objeto* fuera una instancia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4537 y se muestra cómo corregirlo:

```cpp
// C4537.cpp
// compile with: /W1 /c
// processor: x86
struct S {
    int member;
};

void f1(S &s) {
    __asm mov eax, s.member;   // C4537
    // try the following code instead
    // or, make the declaration "void f1(S s)"
    /*
    mov eax, s
    mov eax, [eax]s.member
    */
}
```
