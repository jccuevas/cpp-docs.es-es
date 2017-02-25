---
title: "__getcallerseflags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_getcallerseflags"
  - "_getcallerseflags_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getcallerseflags (función intrínseca)"
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# __getcallerseflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Devuelve el valor de EFLAGS de contexto del llamador.  
  
## Sintaxis  
  
```  
unsigned int __getcallerseflags(void);  
```  
  
## Valor devuelto  
 Valor de EFLAGS de contexto del llamador.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__getcallerseflags`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// getcallerseflags.cpp  
// processor: x86, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__getcallerseflags)  
  
unsigned int g()  
{  
    unsigned int EFLAGS = __getcallerseflags();  
    printf_s("EFLAGS 0x%x\n", EFLAGS);  
    return EFLAGS;  
}  
unsigned int f()  
{  
    return g();  
}  
  
int main()  
{  
    unsigned int i;  
    i = f();  
    i = g();  
    return 0;  
}  
```  
  
  **EFLAGS 0x202 EFLAGS 0x206**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)