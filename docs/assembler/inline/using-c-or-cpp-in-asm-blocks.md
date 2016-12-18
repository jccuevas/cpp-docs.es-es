---
title: "Usar C o C++ en bloques __asm | Microsoft Docs"
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
  - "comentarios, en bloques __asm"
  - "constantes, en bloques __asm"
  - "ensamblado en línea, mezclar instrucciones con instrucciones de C/C++"
  - "macros, __asm (bloques)"
  - "directivas de preprocesador"
  - "directivas de preprocesador, uso en bloques __asm"
  - "preprocesador, directivas"
  - "símbolos, en bloques __asm"
  - "nombres de tipos, uso en bloques __asm"
  - "typedef (nombres), uso en bloques __asm"
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar C o C++ en bloques __asm
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Puesto que las instrucciones de ensamblado insertado se pueden combinar con instrucciones de C o C\+\+, pueden hacer referencia a variables de C o C\+\+ por nombre y usar muchos otros elementos de esos lenguajes.  
  
 Un bloque `__asm` puede usar los elementos de lenguaje siguientes:  
  
-   Símbolos, incluidos etiquetas y nombres de variable y de función  
  
-   Constantes, incluidas constantes simbólicas y miembros de `enum`  
  
-   Macros y directivas de preprocesador  
  
-   Comentarios \(tanto **\/\* \*\/** como **\/\/** \)  
  
-   Nombres de tipo \(dondequiera que un tipo MASM sea legal\)  
  
-   Nombres de`typedef`, utilizados normalmente con operadores tales como **PTR** y **TYPE** o especificar miembros de estructura o unión  
  
 Dentro de un bloque `__asm`, puede especificar constantes de tipo entero con notación C o notación de base de ensamblador \(0x100 y 100h son equivalentes, por ejemplo\).  Esto permite definir \(mediante `#define`\) una constante en C y, a continuación, usarla en C o C\+\+ y en partes de ensamblado del programa.  También puede especificar constantes en octal precediéndolas con un 0.  Por ejemplo, 0777 especifica una constante octal.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Uso de operadores en bloques \_\_asm](../../assembler/inline/using-operators-in-asm-blocks.md)  
  
-   [Uso de símbolos de C o C\+\+ en bloques \_\_asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)  
  
-   [Acceso a datos de C o C\+\+ en bloques \_\_asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)  
  
-   [Escribir funciones con ensamblado alineado](../../assembler/inline/writing-functions-with-inline-assembly.md)  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Ensamblador alineado](../../assembler/inline/inline-assembler.md)