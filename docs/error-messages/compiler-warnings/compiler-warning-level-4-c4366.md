---
title: Advertencia del compilador (nivel 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: fb4cead9367c5ef69627f607c521f480ad94271f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991053"
---
# <a name="compiler-warning-level-4-c4366"></a>Advertencia del compilador (nivel 4) C4366

El resultado del operador ' Operator ' unario puede no estar alineado

Si un miembro de estructura se pudiera desalinear alguna vez debido al empaquetado, el compilador advertirá cuando la dirección de ese miembro se asigne a un puntero alineado. De forma predeterminada, todos los punteros están alineados.

Para resolver C4366, cambie la alineación de la estructura o declare el puntero con la palabra clave [__unaligned](../../cpp/unaligned.md) .

Para obtener más información, vea __unaligned y [Pack](../../preprocessor/pack.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4366.

```cpp
// C4366.cpp
// compile with: /W4 /c
// processor: IPF x64
#pragma pack(1)
struct X {
   short s1;
   int s2;
};

int main() {
   X x;
   short * ps1 = &x.s1;   // OK
   int * ps2 = &x.s2;   // C4366
}
```
