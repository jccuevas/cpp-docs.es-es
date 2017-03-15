---
title: "__readeflags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readeflags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readeflags (función intrínseca)"
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __readeflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Lee el registro de estado y control de programa \(EFLAGS\).  
  
## Sintaxis  
  
```  
unsigned     int __readeflags(void);  
unsigned __int64 __readeflags(void);  
```  
  
## Valor devuelto  
 El valor del registro de EFLAGS.  El valor devuelto es 32 bits long en una plataforma de 32 bits y 64 bits long en una plataforma de 64 bits.  
  
## Comentarios  
 Estas rutinas solo están disponibles como intrínseco.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__readeflags`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_writeeflags](../intrinsics/writeeflags.md)