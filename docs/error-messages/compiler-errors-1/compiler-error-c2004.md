---
title: Error del compilador C2004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2004
dev_langs:
- C++
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b560ef96c4fadcb7c5ce57ece13647032ca9e902
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118757"
---
# <a name="compiler-error-c2004"></a>Error del compilador C2004

se esperaba 'defined(id)'

Debe aparecer un identificador en los paréntesis que siguen a la palabra clave del preprocesador.

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio. NET 2003: faltan paréntesis en la directiva del preprocesador. Si no existe paréntesis de cierre de una directiva de preprocesador, el compilador generará un error.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2004:

```
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

Posible resolución:

```
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