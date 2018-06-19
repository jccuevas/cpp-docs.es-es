---
title: Las herramientas del vinculador LNK4217 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4217
dev_langs:
- C++
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 625f3a1b8a67f198b1cb4ca37bd1350229ec20db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300581"
---
# <a name="linker-tools-warning-lnk4217"></a>Advertencia de las herramientas del vinculador LNK4217
el símbolo 'symbol' importado en la función 'function' definido localmente  
  
 [__declspec (dllimport)](../../cpp/dllexport-dllimport.md) se especificó un símbolo, aunque el símbolo está definido localmente. Quitar el `__declspec` modificador para resolver esta advertencia.  
  
 `symbol` es el nombre del símbolo que se define dentro de la imagen. `function` es la función que importa el símbolo.  
  
 Esta advertencia no aparecerá cuando se compila con la opción [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 LNK4217 también puede producirse si intenta vincular dos módulos juntos, cuando en su lugar, compile el segundo módulo con la biblioteca de importación del primer módulo.  
  
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
  
 Al intentar vincular estos dos módulos suponga LNK4217, compile el segundo ejemplo con la biblioteca de importación del primer ejemplo para resolver.