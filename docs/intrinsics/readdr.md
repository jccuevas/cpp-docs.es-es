---
title: "__readdr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readdr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readdr (función intrínseca)"
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __readdr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Lee el valor del registro especificado de depuración.  
  
## Sintaxis  
  
```  
unsigned         __readdr(unsigned int DebugRegister);  
unsigned __int64 __readdr(unsigned int DebugRegister);  
```  
  
#### Parámetros  
 \[in\] `DebugRegister`  
 Una constante comprendidos entre 0 y 7 que identifica el registro de depuración.  
  
## Valor devuelto  
 El valor del registro especificado de depuración.  
  
## Comentarios  
 Estos intrínseco solo están disponibles en modo kernel, y rutinas solo están disponibles como intrínseco.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__readdr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_readeflags](../intrinsics/readeflags.md)