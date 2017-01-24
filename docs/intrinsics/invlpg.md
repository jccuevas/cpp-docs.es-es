---
title: "__invlpg | Microsoft Docs"
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
  - "__invlpg"
  - "__invlpg_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invlpg (instrucción)"
  - "__invlpg (función instrínseca)"
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __invlpg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción x86 `invlpg` , que reemplaza el búfer almacenamiento de traducción \(TLB\) para la página asociada con memoria designada por a `Address`.  
  
## Sintaxis  
  
```  
void __invlpg(  
   void* Address  
);  
```  
  
#### Parámetros  
 \[in\] `Address`  
 Una dirección de 64 bits.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__invlpg`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 `__invlpg` intrínseco emite una instrucción privilegiada y sólo está disponible en modo kernel con un nivel de privilegios \(CPL\) de 0.  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)