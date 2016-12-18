---
title: "__writecr3 | Microsoft Docs"
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
  - "_writecr3"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_writecr3 (función instrínseca)"
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writecr3
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Escriba el valor `Data` en el registro CR3.  
  
## Sintaxis  
  
```  
void writecr3(   
   unsigned __int64 Data   
);  
```  
  
#### Parámetros  
 \[in\] `Data`  
 El valor a escribir en el registro CR3.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__writecr3`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco sólo está disponible en modo kernel, y la rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)