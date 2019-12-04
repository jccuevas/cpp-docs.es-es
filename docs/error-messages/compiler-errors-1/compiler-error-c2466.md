---
title: Error del compilador C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: aba4de518b9296fadc4746540e4e738c74908617
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743827"
---
# <a name="compiler-error-c2466"></a>Error del compilador C2466

no se puede asignar una matriz de tamaño constante 0

Una matriz se asigna o se declara con el tamaño cero. La expresión constante para el tamaño de la matriz debe ser un entero mayor que cero. Una declaración de matriz con un subíndice cero solo es válida para una clase, una estructura o un miembro de Unión y solo con las extensiones de Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)).

En el ejemplo siguiente se genera C2466:

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
