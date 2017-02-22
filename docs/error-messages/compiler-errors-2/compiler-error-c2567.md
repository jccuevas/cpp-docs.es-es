---
title: "Error del compilador C2567 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2567"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2567"
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error del compilador C2567
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se pueden abrir los metadatos de 'archivo', el archivo se puede haber eliminado o movido  
  
 El proceso de back\-end del compilador no encontró un archivo de metadatos al que se hacía referencia en el código fuente \(con `#using`\) en el mismo directorio que el proceso de front\-end del compilador.  Para obtener más información, vea [\#using \(Directiva\)](../../preprocessor/hash-using-directive-cpp.md).  
  
 El error C2567 se podría producir si se compila con **\/c** en un equipo y luego se intenta generar código en tiempo de vínculo en otro equipo.  Para obtener más información, vea [\/LTCG \(Generación de código en tiempo de enlace\)](../../build/reference/ltcg-link-time-code-generation.md).  
  
 También podría indicar que no quedaba memoria en el equipo.  
  
 Para corregir este error, asegúrese de que el archivo de metadatos está en la misma ubicación del directorio para todas las fases del proceso de compilación.