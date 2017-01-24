---
title: "Usar s&#237;mbolos de C o C++ en bloques __asm | Microsoft Docs"
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
  - "__asm (palabra clave) [C++], elementos de C/C++ en"
  - "__asm (palabra clave) [C++], sintaxis"
  - "símbolos, en bloques __asm"
  - "Visual C, símbolos en bloques __asm"
  - "Visual C++, en bloques __asm"
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar s&#237;mbolos de C o C++ en bloques __asm
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Un bloque `__asm` puede hacer referencia a cualquier símbolo de C o C\+\+ en el ámbito donde aparece el bloque. \(Los símbolos de C y C\+\+ son nombres de variable, nombres de función y etiquetas; es decir, nombres que no sean constantes simbólicas ni miembros de `enum`.  No se puede llamar a funciones miembro de C\+\+\).  
  
 Se aplican algunas restricciones al uso de los símbolos de C y C\+\+:  
  
-   Cada instrucción del lenguaje de ensamblado solo puede contener un símbolo de C o C\+\+.  Pueden aparecer varios símbolos en la misma instrucción de ensamblado solo con las expresiones **LENGTH**, **TYPE** y **SIZE**.  
  
-   Las funciones a las que se hace referencia en un bloque `__asm` se deben declarar antes \(mediante prototipo\) en el programa.  De lo contrario, el compilador no podrá distinguir los nombres de función y las etiquetas en el bloque `__asm`.  
  
-   En un bloque `__asm` no puede haber ningún símbolo de C o C\+\+ escrito igual que las palabras reservadas de MASM \(independientemente de si es en mayúsculas o minúsculas\).  Las palabras reservadas de MASM incluyen nombres de instrucciones, como **PUSH**, y nombres de registro, como SI.  
  
-   Las etiquetas de estructura y unión no se reconocen en los bloques `__asm`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar C o C\+\+ en bloques \_\_asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)