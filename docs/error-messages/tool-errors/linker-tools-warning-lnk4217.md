---
title: "Advertencia de las herramientas del vinculador LNK4217 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4217"
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Advertencia de las herramientas del vinculador LNK4217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se importó el símbolo 'symbol' definido localmente en la función 'function'  
  
 [Se especificó \_\_declspec\(dllimport\)](../../cpp/dllexport-dllimport.md) para un símbolo, aun cuando el símbolo estaba definido localmente.  Quite el modificador `__declspec` para resolver esta advertencia.  
  
 `symbol` es el nombre del símbolo que está definido dentro de la imagen.  `function` es la función que importa el símbolo.  
  
 Esta advertencia no aparecerá cuando se compile con la opción [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 También puede producirse la advertencia LNK4217 si se intentan vincular dos módulos juntos, cuando lo que debería hacerse, en lugar de esto último, es compilar el segundo módulo con la biblioteca de importación del primer módulo.  
  
```  
// LNK4217.cpp  
// compile with: /LD  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 Y, a continuación,  
  
```  
// LNK4217b.cpp  
// compile with: /c  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 Al intentar vincular estos dos módulos se producirá la advertencia LNK4217; compile el segundo ejemplo con la biblioteca de importación del primer ejemplo para resolver la advertencia.