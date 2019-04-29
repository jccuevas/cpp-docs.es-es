---
title: Error del compilador C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 622e7366dda4cd6693d9b6128855fa0966e07952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222484"
---
# <a name="compiler-error-c3320"></a>Error del compilador C3320

'tipo': el tipo no puede tener el mismo nombre que la propiedad de módulo 'nombre'

Un definido por el usuario tipo exportado (UDT), lo que sería una estructura, clase, enumeración o unión, no puede tener el mismo nombre que el parámetro pasado a la [módulo](../../windows/module-cpp.md) propiedad de nombre del atributo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3320:

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```