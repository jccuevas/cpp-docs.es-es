---
title: Compilador advertencia (nivel 4) C4366 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4366
dev_langs:
- C++
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb24c65605857124edf608bec88f1399d9df607d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047049"
---
# <a name="compiler-warning-level-4-c4366"></a>Advertencia del compilador (nivel 4) C4366

El resultado del operador 'operador' unario se puede desalinear

Si un miembro de estructura podría ser nunca sin alinear debido al empaquetado, el compilador le avisará cuando que se asigna la dirección del miembro a un puntero alineado. De forma predeterminada, todos los punteros están alineados.

Para resolver C4366, cambiar la alineación de la estructura o declare el puntero con el [__unaligned](../../cpp/unaligned.md) palabra clave.

Para obtener más información, vea __unaligned y [pack](../../preprocessor/pack.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4366.

```
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