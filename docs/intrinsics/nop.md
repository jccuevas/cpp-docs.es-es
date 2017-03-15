---
title: "__nop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nop (instrucción)"
  - "__nop (función intrínseca)"
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __nop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera código máquina específicas que no realiza ninguna operación.  
  
## Sintaxis  
  
```  
void __nop();  
```  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__nop`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Comentarios  
 La función de `__nop` es equivalente a la instrucción máquina de `NOP` .  Para obtener más información, busque el documento, “Manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones,” en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_noop](../intrinsics/noop.md)