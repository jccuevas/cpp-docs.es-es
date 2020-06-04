---
title: Error del compilador C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 87b5afe2133bb737a8f9c855b0652c2f50ca27ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740525"
---
# <a name="compiler-error-c2601"></a>Error del compilador C2601

' función ': las definiciones de función local no son válidas

El código intenta definir una función dentro de una función.

O bien, puede haber una llave adicional en el código fuente antes de la ubicación del error C2601.

En el ejemplo siguiente se genera C2601:

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```
