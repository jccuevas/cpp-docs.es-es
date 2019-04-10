---
title: Advertencia de las herramientas del vinculador LNK4217
ms.date: 04/09/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 3fcb806afa064a4f6d9c9c0680c617662a3b9a21
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477397"
---
# <a name="linker-tools-warning-lnk4217"></a>Advertencia de las herramientas del vinculador LNK4217

> símbolo '*símbolo*'definido en'*filename_1.obj*'se importa de forma'*filename_2.obj*'en la función'*función*'

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó para un símbolo, aunque el símbolo está definido en un archivo de objeto en la misma imagen. Quitar el `__declspec(dllimport)` modificador para resolver esta advertencia.

*símbolo* es el nombre del símbolo que se define dentro de la imagen. *función* es la función que se importa el símbolo.

Esta advertencia no aparece cuando se compila con la [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opción.

LNK4217 también puede producirse si intenta vincular dos módulos juntos, cuando en su lugar, debe compilar el segundo módulo con la biblioteca de importación del primer módulo.

```cpp
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Y luego,

```cpp
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Al intentar vincular estos dos módulos se producirá en LNK4217. Compile el segundo ejemplo con la biblioteca de importación de la primera muestra a resolver.