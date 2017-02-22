---
title: "Directivas de datos y operadores en los ensamblados alineados | Microsoft Docs"
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
  - "__asm (palabra clave) [C++], hacer referencia a limitaciones"
  - "directivas de datos [C++]"
  - "directivas [C++], MASM"
  - "ensamblado en línea, directivas de datos"
  - "ensamblado en línea, operadores"
  - "MASM (Microsoft Macro Assembler), directivas"
  - "MASM (Microsoft Macro Assembler), operadores"
  - "MASM (Microsoft Macro Assembler), estructuras"
  - "operadores [MASM]"
  - "estructuras [C++], MASM"
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Directivas de datos y operadores en los ensamblados alineados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Aunque un bloque `__asm` puede hacer referencia a tipos de datos y objetos de C o C\+\+, no puede definir objetos de datos con directivas u operadores de MASM.  Específicamente, no se pueden utilizar las directivas de definición **DB**, `DW`, **DD**, `DQ`, `DT` y `DF`, ni los operadores `DUP` o **THIS**.  Las estructuras y los registros de MASM tampoco están disponibles.  El código ensamblador alineado no acepta las directivas `STRUC`, `RECORD`, **WIDTH** o **MASK**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)