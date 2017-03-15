---
title: "__writedr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__writedr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__writedr (función intrínseca)"
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __writedr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Escriba el valor especificado en el registro especificado de depuración.  
  
## Sintaxis  
  
```  
void __writedr(unsigned DebugRegister, unsigned DebugValue);  
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);  
```  
  
#### Parámetros  
 \[in\] `DebugRegister`  
 Un número de 0 a 7 que identifica el registro de depuración.  
  
 \[in\]`DebugValue`  
 Un valor a escribir en el registro de depuración.  
  
## Comentarios  
 Estos intrínseco solo están disponibles en modo kernel, y rutinas solo están disponibles como intrínseco.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__writedr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_readdr](../intrinsics/readdr.md)