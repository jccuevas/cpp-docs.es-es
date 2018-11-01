---
title: Error del compilador C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: 425d1bf50d56c4455ccd9292b300e744625d34c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638417"
---
# <a name="compiler-error-c2970"></a>Error del compilador C2970

'class': parámetro de plantilla 'param': 'arg': no se puede usar una expresión que contenga objetos con vinculación interna como un argumento sin tipo

No se puede usar el nombre o dirección de una variable estática como argumento de plantilla. La clase de plantilla espera un valor constante que se puede evaluar en tiempo de compilación.

El ejemplo siguiente genera C2970:

```
// C2970.cpp
// compile with: /c
static int si;
// could declare nonstatic to resolve all errors
// int si;

template <int i>
class X {};

template <int *pi>
class Y {};

X<si> anX;   // C2970 cannot use static variable in templates

// this would also work
const int i = 10;
X<i> anX2;
```