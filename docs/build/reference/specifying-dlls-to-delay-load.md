---
title: Especificar archivos DLL para carga retrasada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e9becc0a686d3add5db140b239f1997f81a45be
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722584"
---
# <a name="specifying-dlls-to-delay-load"></a>Especificar archivos DLL para carga retrasada

Puede especificar qué archivos DLL retrasar la carga con el [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md):`dllname` opción del vinculador. Si no piensa usar su propia versión de una función auxiliar, también debe vincular el programa con delayimp.lib (para aplicaciones de escritorio) o dloadhelper.lib (para aplicaciones de la tienda).

El siguiente es un ejemplo sencillo de retraso de la carga de un archivo DLL:

```
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

Genera la versión de depuración del proyecto. Recorra el código usando el depurador y observará que el archivo user32.dll solo se carga cuando realiza la llamada a `MessageBox`.

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)