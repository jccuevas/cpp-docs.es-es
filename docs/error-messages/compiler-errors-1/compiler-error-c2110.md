---
title: Error del compilador C2110
ms.date: 11/04/2016
f1_keywords:
- C2110
helpviewer_keywords:
- C2110
ms.assetid: 48fd76ed-90d6-4a60-9c7b-f6ce9355b4ca
ms.openlocfilehash: 91c674623624f4c156376faffd6aeae804a9308d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741201"
---
# <a name="compiler-error-c2110"></a>Error del compilador C2110

'+': no se pueden sumar dos punteros

Se intentaron agregar dos valores de puntero con el operador más ( `+` ).

El ejemplo siguiente genera la advertencia C2110:

```cpp
// C2110.cpp
int main() {
   int a = 0;
   int *pa;
   int *pb;
   a = pa + pb;   // C2110
}
```
