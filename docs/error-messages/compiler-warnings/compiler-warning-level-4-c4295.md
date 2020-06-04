---
title: Advertencia del compilador (nivel 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: 5e8b546e4eb4b60197db504382b3230e779b1dec
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924851"
---
# <a name="compiler-warning-level-4-c4295"></a>Advertencia del compilador (nivel 4) C4295

> '*array*': la matriz es demasiado pequeña para incluir un carácter nulo de terminación

Se inicializó una matriz, pero el último carácter de la matriz no es null; el acceso a la matriz como una cadena puede producir resultados inesperados.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4295. Para corregir este problema, puede declarar el tamaño de la matriz más grande, para que contenga un carácter nulo de terminación de la cadena de inicializador, o puede usar una lista de inicializadores de matriz para aclarar que `char`se trata de una matriz de, no una cadena terminada en NULL.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
