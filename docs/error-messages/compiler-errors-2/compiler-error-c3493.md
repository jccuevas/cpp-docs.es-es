---
title: Error del compilador C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: ece70a99477b018f6d7a935911f475e4fb4397cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548010"
---
# <a name="compiler-error-c3493"></a>Error del compilador C3493

'var' no se puede capturar de forma implícita porque no se ha especificado ningún modo de captura predeterminado

La captura de la expresión lambda vacía, `[]`, especifica que la expresión lambda no captura de forma explícita ni implícita ninguna variable.

### <a name="to-correct-this-error"></a>Para corregir este error

- Proporcione un modo de captura predeterminado, o bien

- Capture explícitamente una o varias variables.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3493 porque modifica una variable externa, pero especifica la cláusula de captura vacía:

```
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente resuelve el error C3493 especificando mediante referencia como el modo de captura predeterminado.

```
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)