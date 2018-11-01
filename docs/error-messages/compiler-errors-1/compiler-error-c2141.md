---
title: Error del compilador C2141
ms.date: 11/04/2016
f1_keywords:
- C2141
helpviewer_keywords:
- C2141
ms.assetid: 10cf770f-0500-4220-ac90-a863b7ea5fe6
ms.openlocfilehash: 89395fa3419d79fa4dec3fecf9acfc681590d825
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593991"
---
# <a name="compiler-error-c2141"></a>Error del compilador C2141

desbordamiento de tamaño de matriz

Una matriz que supera el límite de 2GB. Reduzca el tamaño de la matriz.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2141.

```
// C2141.cpp
// processor: IPF
class A {
   short m_n;
};

int main()
{
   A* pA = (A*)(-1);
   pA = new A[0x8000000000000001];   // C2141

   A* pA2 = (A*)(-1);
   pA2 = new A[0x80000000000000F];   // OK
}
```