---
title: "Advertencia de la l&#237;nea de comandos D9041 | Microsoft Docs"
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
  - "D9041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9041"
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de la l&#237;nea de comandos D9041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

valor 'valor' no válido para 'opción'; se supone 'valor'; agregue '\/analyze' a las opciones de la línea de comandos cuando especifique esta advertencia  
  
 Se agregó un número de advertencia de análisis de código a la opción de línea de comandos **\/wd**, **\/we**, **\/wo** o **\/wl** sin especificar también la opción de línea de comandos **\/analyze**.  Para solucionar este error, agregue la opción de línea de comandos **\/analyze** o quite el número de advertencia no válido de la opción de línea de comandos **\/w** correspondiente.  
  
## Ejemplo  
 El ejemplo de línea de comandos siguiente genera la advertencia D9041:  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 La solución es agregar la opción de línea de comandos **\/analyze**.  Si **\/analyze** no se admite en su versión del compilador, quite el número de advertencia no válido de la opción **\/wd**.  
  
## Vea también  
 [Errores de la línea de comandos de D8000 a D9000](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)