---
title: Advertencia de las herramientas del vinculador LNK4217
ms.date: 11/04/2016
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 12766241832d39f0b47ed85036c0ebeb0447fc75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448053"
---
# <a name="linker-tools-warning-lnk4217"></a>Advertencia de las herramientas del vinculador LNK4217

el símbolo 'symbol' importado en la función 'función' definido localmente

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para un símbolo, aunque el símbolo está definido localmente. Quitar el `__declspec` modificador para resolver esta advertencia.

`symbol` es el nombre del símbolo que se define dentro de la imagen. `function` es la función que se importa el símbolo.

Esta advertencia no aparecerá cuando se compila con la opción [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

LNK4217 también puede producirse si intenta vincular dos módulos juntos, cuando en su lugar, debe compilar el segundo módulo con la biblioteca de importación del primer módulo.

```
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Y luego,

```
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Al intentar vincular estos dos módulos suponga LNK4217, compile el segundo ejemplo con la biblioteca de importación de la primera muestra a resolver.