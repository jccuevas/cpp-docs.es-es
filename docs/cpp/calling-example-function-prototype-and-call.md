---
title: 'Ejemplo de llamada: Prototipo de función y llamada'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: c41d7679be8b7faa3c8df1368d14815a1b840284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190175"
---
# <a name="calling-example-function-prototype-and-call"></a>Ejemplo de llamada: Prototipo de función y llamada

**Específicos de Microsoft**

En el ejemplo siguiente se muestran los resultados de realizar una llamada de función mediante diversas convenciones de llamada.

Este ejemplo está basado en el esqueleto de función siguiente. Reemplace `calltype` por la convención de llamada adecuada.

```cpp
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

Para obtener más información, vea [resultados del ejemplo de llamada](../cpp/results-of-calling-example.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Convenciones de llamada](../cpp/calling-conventions.md)
