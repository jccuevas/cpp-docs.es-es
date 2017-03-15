---
title: "__wbinvd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__wbinvd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__wbinvd (función intrínseca)"
  - "wbinvd (instrucción)"
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __wbinvd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la reproducción de escritura y reemplaza la instrucción de caché \(`wbinvd`\).  
  
## Sintaxis  
  
```  
void __wbinvd(void);  
```  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__wbinvd`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta función solo está disponible en modo kernel con un nivel de privilegios \(CPL\) de 0, y la rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)