---
title: Especificar archivos DLL para carga retrasada
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: 2b6737abd76c03186881e83bbd2bf286be6ffe2f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813232"
---
# <a name="specifying-dlls-to-delay-load"></a>Especificar archivos DLL para carga retrasada

Puede especificar qué archivos DLL retrasar la carga con el [/DELAYLOAD](delayload-delay-load-import.md):`dllname` opción del vinculador. Si no piensa usar su propia versión de una función del asistente, también debe vincular el programa con delayimp.lib (para aplicaciones de escritorio) o dloadhelper.lib (para aplicaciones de la tienda).

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

[Compatibilidad del vinculador con las DLL de carga retrasada](linker-support-for-delay-loaded-dlls.md)
