---
title: -IMPORTS (DUMPBIN) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /imports
dev_langs:
- C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af3b9a1bbcf1769e87715e46566dee9c53a96747
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)
```  
/IMPORTS[:file]  
```  
  
 Esta opción muestra la lista de archivos DLL (tanto los vinculados estáticamente y [cargado retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)) que se importan en un archivo ejecutable o DLL y todas las importaciones individuales de cada uno de estos archivos DLL.  
  
 Opcional `file` especificación le permite especificar que se mostrarán las importaciones para únicamente ese archivo DLL. Por ejemplo:  
  
```  
dumpbin /IMPORTS:msvcrt.dll  
```  
  
## <a name="remarks"></a>Comentarios  
 Los resultados mostrados por esta opción son similar a la [/EXPORTS](../../build/reference/dash-exports.md) salida.  
  
 Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)