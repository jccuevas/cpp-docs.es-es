---
title: "__inbyte | Microsoft Docs"
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
  - "__inbyte"
  - "__inbyte_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "in (instrucción)"
  - "__inbyte (función intrínseca)"
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __inbyte
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `in` , devolviendo una lectura de byte puerto especificado por `Port`.  
  
## Sintaxis  
  
```  
unsigned char __inbyte(  
   unsigned short Port  
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto de lectura.  
  
## Valor devuelto  
 La lectura de byte puerto especificado.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__inbyte`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Específico de Microsoft de FINAL  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)