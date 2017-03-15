---
title: "Comentarios del lenguaje ensamblador | Microsoft Docs"
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
  - "__asm (palabra clave) [C++], instrucciones"
  - "lenguaje ensamblador [C++], comentarios"
  - "comentarios [C++], lenguaje ensamblador"
  - "macros [C++], lenguaje ensamblador"
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Comentarios del lenguaje ensamblador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Las instrucciones en un bloque `__asm` pueden utilizar comentarios en lenguaje de ensamblado:  
  
```  
__asm mov ax, offset buff ; Load address of buff  
```  
  
 Debido a que las macros de C se expanden en una única línea lógica, evite utilizar comentarios en lenguaje de ensamblado en las macros. \(Vea [Definición de bloques \_\_asm como macros de C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)\). Un bloque `__asm` también puede contener comentarios del tipo de C; para obtener más información, vea [Uso de C o C\+\+ en bloques \_\_asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)