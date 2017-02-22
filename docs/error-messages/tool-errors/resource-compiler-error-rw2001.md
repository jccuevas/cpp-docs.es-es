---
title: "Error del compilador de recursos RW2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2001"
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador de recursos RW2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Directiva no válida en el archivo RC preprocesado  
  
 El archivo RC contiene una directiva **\#pragma**.  
  
 Utilice la directiva de preprocesador **\#ifndef** con la constante **RC\_INVOKED** que define el compilador de recursos cuando se procesa un archivo de inclusión.  Sitúe la directiva **\#pragma** dentro de un bloque de código no procesado cuando se defina la constante **RC\_INVOKED**.  El código del bloque sólo se procesa mediante el compilador C\/C\+\+ y no mediante el compilador de recursos.  El ejemplo siguiente muestra esta técnica:  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 La directiva de preprocesador **\#pragma** carece de significado en un archivo .RC.  La directiva de preprocesador **\#include** se usa con frecuencia en un archivo .RC para incluir un archivo de encabezado \(ya sea uno personalizado basado en un proyecto o uno estándar de Microsoft incluido en uno de sus productos\).  Algunos de estos archivos de inclusión contienen la directiva **\#pragma**.  Debido a que el archivo de encabezado puede incluir uno o más archivos de encabezado, el archivo que contiene la directiva **\#pragma** que causa el error puede no ser tan evidente.  
  
 La técnica **\#ifndefRC\_INVOKED** puede controlar archivos de encabezado de inclusión en archivos de encabezado basados en proyectos.