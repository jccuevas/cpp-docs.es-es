---
title: ADVERTENCIA del compilador (nivel 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 326b73dcf4665c442926e68995bace60300b6ebf
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052099"
---
# <a name="compiler-warning-level-2-c4285"></a>ADVERTENCIA del compilador (nivel 2) C4285

el tipo de valor devuelto para ' Identifier:: Operator-> ' es recursivo si se aplica mediante una notación infija

La función **Operator-> ()** especificada no puede devolver el tipo para el que se define o una referencia al tipo para el que se define.

En el ejemplo siguiente se genera C4285:

```cpp
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```