---
title: Error del compilador C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 6fe4286142c90f341925d7e76ca8de6d3b7daa9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075010"
---
# <a name="compiler-error-c3495"></a>Error del compilador C3495

'var': una captura lambda debe tener una duración de almacenamiento automática

No se puede capturar una variable que no tiene una duración de almacenamiento automática, como una variable que está marcada como `static` o `extern`.

### <a name="to-correct-this-error"></a>Para corregir este error

- No pase una variable `static` o `extern` a la lista de captura de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3495 porque la variable de `static``n` aparece en la lista de captura de una expresión lambda:

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Consulte también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)
