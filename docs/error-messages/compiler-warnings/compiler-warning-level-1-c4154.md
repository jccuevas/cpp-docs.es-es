---
title: ADVERTENCIA del compilador (nivel 1) C4154
ms.date: 11/04/2016
f1_keywords:
- C4154
helpviewer_keywords:
- C4154
ms.assetid: 4511afeb-e893-4cc6-83b6-4c7a0477f76b
ms.openlocfilehash: 07b4c6e0821c925e70ce1bce1d910f184d658982
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163617"
---
# <a name="compiler-warning-level-1-c4154"></a>ADVERTENCIA del compilador (nivel 1) C4154

eliminación de una expresión de matriz; conversión al puntero proporcionado

No se puede usar `delete` en una matriz, por lo que el compilador convierte la matriz en un puntero.

## <a name="example"></a>Ejemplo

```cpp
// C4154.cpp
// compile with: /c /W1
int main() {
   int array[ 10 ];
   delete array;   // C4154 can't delete stack object

   int *parray2 = new int [10];
   int (&array2)[10] = (int(&)[10]) parray2;
   delete [] array2;   // C4154

   // try the following line instead
   delete [] &array2;
}
```
