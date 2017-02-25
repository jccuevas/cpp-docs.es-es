---
title: "Error irrecuperable C1352 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1352"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1352"
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable C1352
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MSIL no válido o dañado en la función 'function' del módulo 'file'  
  
 Se pasó un archivo .netmodule al compilador, pero el compilador detectó daños en el archivo.  Pida a la persona que generó el archivo .netmodule que lo investigue.  
  
 El compilador no comprueba los archivos .netmodule en busca de todos los tipos de daños.  Sin embargo, comprueba que todas las rutas de control de una función contengan una instrucción return.  
  
 Para más información, consulte [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).