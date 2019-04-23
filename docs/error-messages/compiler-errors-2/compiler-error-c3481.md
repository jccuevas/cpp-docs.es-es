---
title: Error del compilador C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: eff7c7a4f39524aa1d894b7b4590aa809714aae6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041207"
---
# <a name="compiler-error-c3481"></a>Error del compilador C3481

'var': no se encuentra la variable de captura lambda

El compilador no puede encontrar la definición de una variable que se pasó a la lista de capturas de una expresión lambda.

### <a name="to-correct-this-error"></a>Para corregir este error

- Quite la variable de la lista de capturas de la expresión lambda.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3481 porque la variable `n` no está definida:

```
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Vea también

[Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)