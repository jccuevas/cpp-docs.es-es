---
title: 'Ejemplo de llamada: Prototipo de función y llamada'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: cbe9ee16db502c9e27dcbd74da4ef6a85f00960f
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857637"
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

## <a name="see-also"></a>Vea también

[Convenciones de llamada](../cpp/calling-conventions.md)