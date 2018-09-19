---
title: Error del compilador C2675 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2675
dev_langs:
- C++
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1772f6e88516e7c8c1498f84d180ab6c4e0e05ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102413"
---
# <a name="compiler-error-c2675"></a>Error del compilador C2675

'operador' unario: 'tipo' no define este operador o una conversión a un tipo aceptable para el operador predefinido

C2675 también puede producirse al usar un operador unario y el tipo no define el operador o una conversión a un tipo aceptable para el operador predefinido. Para usar este operador, debe sobrecargarlo para el tipo especificado o definir una conversión a un tipo para el que esté definido el operador.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2675.

```
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```