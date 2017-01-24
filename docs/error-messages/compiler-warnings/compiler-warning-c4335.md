---
title: "Advertencia del compilador C4335 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4335"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4335"
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4335
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Formato de archivo Mac detectado: convierta el archivo de código fuente en formato DOS o UNIX  
  
 El carácter de fin de línea de la primera línea de un archivo de origen es de estilo Macintosh \('\\r'\), en contraposición a UNIX \('\\n'\) o DOS \('\\r\\n'\).  
  
 Esta advertencia siempre se emite como un error.  Vea la directiva pragma [warning](../../preprocessor/warning.md) para obtener información sobre cómo deshabilitar esta advertencia.  Además, esta advertencia sólo se muestra una vez por compilación.  Por lo tanto, si hay varias directivas `#include` que especifican archivos en formato Macintosh, C4335 solo se emitirá una vez.  
  
 Una manera de generar archivos en formato Macintosh es usar **Opciones avanzadas para guardar** \(menú **Archivo**\) en Visual Studio.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4335.  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```