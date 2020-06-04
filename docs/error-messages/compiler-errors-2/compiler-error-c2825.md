---
title: Error del compilador C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 6a51901477958056356a96d71adde4241d60a2ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750590"
---
# <a name="compiler-error-c2825"></a>Error del compilador C2825

var: debe ser una clase o un espacio de nombres cuando va seguido de ':: '

Se intentó crear un nombre completo.

Por ejemplo, asegúrese de que el código no contiene una declaración de función en la que el nombre de función comienza por::.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2825:

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
