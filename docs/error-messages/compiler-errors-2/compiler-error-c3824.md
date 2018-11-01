---
title: Error del compilador C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: d7c55ede285d027b1a65b33adbf6407df243f068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635644"
---
# <a name="compiler-error-c3824"></a>Error del compilador C3824

'member': este tipo no puede aparecer en este contexto (parámetro de función, tipo de valor devuelto o un miembro estático)

Punteros anclados no pueden ser parámetros de función, tipos de valor devuelto o declara `static`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3824:

```
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```
