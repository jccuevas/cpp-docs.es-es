---
title: "Error irrecuperable C1107 | Microsoft Docs"
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
  - "C1107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1107"
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se encuentra el ensamblado 'archivo': especifique la ruta de acceso de búsqueda del ensamblado utilizando \/AI o estableciendo la variable de entorno LIBPATH  
  
 El compilador no pudo encontrar un archivo de metadatos pasado a una directiva [\#using](../../preprocessor/hash-using-directive-cpp.md).  
  
 LIBPATH \(que se describe en el tema dedicado a `#using`\) y la opción del compilador [\/AI](../../build/reference/ai-specify-metadata-directories.md) permiten especificar los directorios en los que el compilador deberá buscar los archivos de metadatos a los que se haga referencia.