---
title: "__readmsr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readmsr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Leer el registro específico del modelo"
  - "rdmsr (instrucción)"
  - "__readmsr (función intrínseca)"
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __readmsr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `rdmsr` , que lee el registro modelo\-específico especificado por `register` y devuelve su valor.  
  
## Sintaxis  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### Parámetros  
 \[in\] `register`  
 El registro concreto modelo a leer.  
  
## Valor devuelto  
 El valor del registro especificado.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__readmsr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta función solo está disponible en modo kernel, y la rutina sólo está disponible como intrínseco.  
  
 Para obtener más información, vea la documentación de AMD.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)