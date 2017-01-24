---
title: "__writeeflags | Microsoft Docs"
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
  - "__writeeflags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__writeeflags (funciones intrínsecas)"
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __writeeflags
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Escriba el valor especificado en el registro de estado y control de programa \(EFLAGS\).  
  
## Sintaxis  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `Value`|El valor a escribir en el registro de EFLAGS.  El parámetro de `Value` es 32 bits long para una plataforma de 32 bits y 64 bits long para una plataforma de 64 bits.|  
  
## Comentarios  
 Estas rutinas solo están disponibles como intrínseco.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__writeeflags`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_readeflags](../intrinsics/readeflags.md)