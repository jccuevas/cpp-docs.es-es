---
title: -IMPORTS (DUMPBIN) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /imports
dev_langs: C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1866c8d522e7482781aa65e58d93ccb09e6b265f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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