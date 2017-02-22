---
title: "__int2c | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__int2c"
  - "__int2c_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "int2c (función intrínseca)"
  - "int 2c (instrucción)"
  - "__int2c (función intrínseca)"
ms.assetid: aa20ff30-adef-42bb-8577-8010f3122f8e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# __int2c
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `int 2c` , que desencadena la interrupción de `2c` .  
  
## Sintaxis  
  
```  
void __int2c(void);  
```  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__int2c`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)