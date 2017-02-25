---
title: "Macros de comando y macros de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros de comandos en NMAKE"
  - "macros, macros de comandos"
  - "macros, macros de opciones"
  - "macros de opciones"
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Macros de comando y macros de opciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las macros de comando están predefinidas para productos de Microsoft.  Las macros de opciones representan opciones para estos productos y no están definidas de forma predeterminada.  Ambos tipos de macros se usan en reglas de inferencia predefinidas y se pueden utilizar en bloques de descripción o en reglas de inferencia definidas por el usuario.  Las macros de comando se pueden volver a definir para representar una parte o la totalidad de una línea de comandos, incluidas las opciones.  Las macros de opciones generan una cadena nula si se dejan sin definir.  
  
|Producto Microsoft|Macro de comando|Definida como|Macro de opciones|  
|------------------------|----------------------|-------------------|-----------------------|  
|Macro Assembler|**AS**|ml|**AFLAGS**|  
|Compilador de Basic|**BC**|bc|**BFLAGS**|  
|Compilador C|**CC**|cl|**CFLAGS**|  
|Compilador de C\+\+|**CPP**|cl|**CPPFLAGS**|  
|Compilador de C\+\+|**CXX**|cl|**CXXFLAGS**|  
|Compilador de recursos|**RC**|cr|**RFLAGS**|  
  
## Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)