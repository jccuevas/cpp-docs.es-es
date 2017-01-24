---
title: "__writecr4 | Microsoft Docs"
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
  - "_writecr4"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_writecr4 (función intrínseca)"
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writecr4
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Escriba el valor `Data` en el registro CR4.  
  
## Sintaxis  
  
```  
void writecr4(   
   unsigned __int64 Data   
);  
```  
  
#### Parámetros  
 \[in\] `Data`  
 El valor a escribir en el registro CR4.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__writecr4`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco sólo está disponible en modo kernel, y la rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)