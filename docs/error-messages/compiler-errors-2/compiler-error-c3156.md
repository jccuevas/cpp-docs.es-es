---
title: Error del compilador C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 115e8cd63562964b19e4a67f7a649ecfab2596c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465265"
---
# <a name="compiler-error-c3156"></a>Error del compilador C3156

'class' : no se puede tener una definición local de un tipo administrado o WinRT

Una función no puede contener la definición o la declaración de un struct, una interfaz o una clase administrada o WinRT.

## <a name="example"></a>Ejemplo

El siguiente ejemplo genera el error C3156.

```
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
