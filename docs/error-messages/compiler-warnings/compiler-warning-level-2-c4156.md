---
title: ADVERTENCIA del compilador (nivel 2) C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: b9add4af0fddf8d68bbba0293530f2bb0ce3800d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162093"
---
# <a name="compiler-warning-level-2-c4156"></a>ADVERTENCIA del compilador (nivel 2) C4156

eliminación de una expresión de matriz sin utilizar el formato de matriz de ' delete '; formulario de matriz sustituido

La forma de **eliminación** que no es de matriz no puede eliminar una matriz. El compilador ha traducido **Delete** al formulario de la matriz.

Esta advertencia solo se produce en las extensiones de Microsoft (/ZE).

## <a name="example"></a>Ejemplo

```cpp
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```
