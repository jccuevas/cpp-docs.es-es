---
title: Error del compilador C3269
ms.date: 11/04/2016
f1_keywords:
- C3269
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
ms.openlocfilehash: 406b388460b3d449471c884dd6461f2ce59a10f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622955"
---
# <a name="compiler-error-c3269"></a>Error del compilador C3269

'function': no se puede declarar una función miembro de tipo administrado o WinRTtype con '...'

Las funciones de miembro de clase administradas y WinRT no pueden declarar listas de parámetros de longitud variable.

El ejemplo siguiente genera el error C3269 y muestra cómo corregirlo:

```
// C3269_2.cpp
// compile with: /clr

ref struct A
{
   void func(int i, ...)   // C3269
   // try the following line instead
   // void func(int i )
   {
   }
};

int main()
{
}
```
