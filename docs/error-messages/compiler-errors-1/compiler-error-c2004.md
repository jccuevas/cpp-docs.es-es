---
title: Error del compilador C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: b781e9f81342f35d66eca222bd338252b739096c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737496"
---
# <a name="compiler-error-c2004"></a>Error del compilador C2004

se esperaba 'defined(id)'

Debe aparecer un identificador en los paréntesis que siguen a la palabra clave del preprocesador.

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio. NET 2003: faltan paréntesis en la directiva del preprocesador. Si no existe paréntesis de cierre de una directiva de preprocesador, el compilador generará un error.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2004:

```cpp
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

## <a name="example"></a>Ejemplo

Solución posible:

```cpp
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```
