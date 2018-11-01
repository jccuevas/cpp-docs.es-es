---
title: Advertencia del compilador (nivel 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 96e1077ce3c9e60823a11aa41719738265ee703b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535985"
---
# <a name="compiler-warning-level-2-c4285"></a>Advertencia del compilador (nivel 2) C4285

tipo de valor devuelto para 'identificador:: operator ->' es recursivo si se aplica utilizando una notación infija

Especificado **operador -> ()** función no puede devolver el tipo para la que está definida o una referencia al tipo para el que está definido.

El ejemplo siguiente genera C4285:

```
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