---
title: Especificar archivos DLL para carga retrasada | Documentos de Microsoft
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
ms.openlocfilehash: a7756499ddf24055feb1c540df13fbe8249edf42
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373727"
---
# <a name="specifying-dlls-to-delay-load"></a>Especificar archivos DLL para carga retrasada
Puede especificar qué archivos DLL para retrasar la cargan con el [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md):`dllname` opción del vinculador. Si no piensa usar su propia versión de una función auxiliar, también debe vincular el programa con delayimp.lib (para aplicaciones de escritorio) o dloadhelper.lib (para aplicaciones de la tienda).  
  
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