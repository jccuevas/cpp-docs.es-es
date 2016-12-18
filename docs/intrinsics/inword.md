---
title: "__inword | Microsoft Docs"
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
  - "__indword_cpp"
  - "__indword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "in (instrucción)"
  - "__inword (función intrínseca)"
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __inword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Lee datos de puerto especificado mediante la instrucción de `in` .  
  
## Sintaxis  
  
```  
unsigned short __inword(  
   unsigned short Port  
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto de lectura.  
  
## Valor devuelto  
 La palabra de la lectura de los datos.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__inword`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)