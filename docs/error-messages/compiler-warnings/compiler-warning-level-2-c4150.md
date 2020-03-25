---
title: ADVERTENCIA del compilador (nivel 2) C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: c4d84165c7fcda4ceab94b1380a818236f6f5ea5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162119"
---
# <a name="compiler-warning-level-2-c4150"></a>ADVERTENCIA del compilador (nivel 2) C4150

eliminación de puntero al tipo incompleto ' type '; no se llamó a ningún destructor

Se llama al operador **Delete** para eliminar un tipo declarado pero no definido, por lo que el compilador no puede encontrar un destructor.

En el ejemplo siguiente se genera C4150:

```cpp
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```
