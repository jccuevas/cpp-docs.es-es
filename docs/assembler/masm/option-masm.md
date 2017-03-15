---
title: "OPTION (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "option"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OPTION directive"
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# OPTION (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita y deshabilita las características de código ensamblador.  
  
## Sintaxis  
  
```  
  
OPTION   
optionlist  
  
```  
  
## Comentarios  
 Disponibles son de opciones:  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULADOR**|  
|**NOEMULATOR**|**EPÍLOGO**|**EXPR16**|**EXPR32**|  
|**LENGUAJE**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**Desplazamiento**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROCEDURE**|**PROLOGUE**|**READONLY**|**NOREADONLY**|  
|**SCOPED**|**NOSCOPED**|**SEGMENTO**|**SETIF2**.|  
  
 La sintaxis para el LENGUAJE es **LENGUAJE OF TABLE OPCIÓN:***x*, donde uno *x* de C, de SYSCALL, de STDCALL, de PASCAL, de FORTRAN, o de BASIC.  SYSCALL, PASCAL, el FORTRAN, y BASIC no se admiten con utilizado con [.MODEL](../../assembler/masm/dot-model.md) FLAT.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)