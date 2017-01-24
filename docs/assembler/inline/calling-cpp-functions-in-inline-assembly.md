---
title: "Llamar a funciones de C++ en ensamblados alineados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm (palabra clave) [C++], llamar a funciones"
  - "llamadas a funciones, funciones de C++"
  - "llamadas a funciones, en ensamblado alineado"
  - "funciones [C++], llamar en ensamblado alineado"
  - "ensamblado en línea, llamar a funciones"
  - "Visual C++, funciones"
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Llamar a funciones de C++ en ensamblados alineados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Un bloque `__asm` solo puede llamar a funciones globales de C\+\+ que no estén sobrecargadas.  Si llama a una función global sobrecargada de C\+\+ o a una función miembro de C\+\+, el compilador genera un error.  
  
 También puede llamar a cualquier función declarada con vinculación **extern de "C"**.  Esto permite que un bloque `__asm` en un programa de C\+\+ llame a las funciones de biblioteca de C, porque todos los archivos de encabezado estándar declaran las funciones de biblioteca con vinculación **extern de "C"**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Ensamblador alineado](../../assembler/inline/inline-assembler.md)