---
title: 'Ejemplo de llamada: Llamada y el prototipo de función'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345111"
---
# <a name="calling-example-function-prototype-and-call"></a>Ejemplo de llamada: Llamada y el prototipo de función

## <a name="microsoft-specific"></a>Específicos de Microsoft

En el ejemplo siguiente se muestran los resultados de realizar una llamada de función mediante diversas convenciones de llamada.

Este ejemplo está basado en el esqueleto de función siguiente. Reemplace `calltype` por la convención de llamada adecuada.

```
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

Para obtener más información, consulte [los resultados de ejemplo de llamada](../cpp/results-of-calling-example.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Convenciones de llamada](../cpp/calling-conventions.md)