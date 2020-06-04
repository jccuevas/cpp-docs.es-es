---
title: Error del compilador C2232
ms.date: 11/04/2016
f1_keywords:
- C2232
helpviewer_keywords:
- C2232
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
ms.openlocfilehash: 78ed8970b29126bceb06ff89d12c83cb98c4b5fd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301813"
---
# <a name="compiler-error-c2232"></a>Error del compilador C2232

'-> ': el operando izquierdo tiene el tipo ' Class-Key ', use '. '

El operando situado a la izquierda del operador `->` no es un puntero. Use el operador de punto (.) para una clase, estructura o Unión.

El ejemplo siguiente genera la advertencia C2232:

```c
// C2232.c
struct X {
    int member;
} x, *px;
int main() {
    x->member = 0;   // C2232, x is not a pointer

    px->member = 0;
    x.member = 0;
}
```
