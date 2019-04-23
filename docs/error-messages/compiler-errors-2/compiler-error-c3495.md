---
title: Error del compilador C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 3e387fe77c521a4f25ba67205f1fbd552397e272
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035827"
---
# <a name="compiler-error-c3495"></a>Error del compilador C3495

'var': una captura lambda debe tener una duración de almacenamiento automática

No se puede capturar una variable que no tiene una duración de almacenamiento automática, como una variable que está marcada como `static` o `extern`.

### <a name="to-correct-this-error"></a>Para corregir este error

- No pase una variable `static` o `extern` a la lista de captura de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3495 porque la variable de `static` `n` aparece en la lista de captura de una expresión lambda:

```
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)

