---
title: Error del compilador C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 6ff269d719dd354932ef79946ae99a9b60490199
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039429"
---
# <a name="compiler-error-c3482"></a>Error del compilador C3482

'this' solo se puede usar como captura lambda en una función miembro no estática

No se puede pasar `this` a la lista de captura de una expresión lambda declarada en un método estático o una función global.

### <a name="to-correct-this-error"></a>Para corregir este error

- Convierta la función de inclusión a un método no estático, o

- Quite el puntero `this` de la lista de captura de la expresión lambda.

## <a name="example"></a>Ejemplo

El siguiente ejemplo genera el error C3482:

```
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)