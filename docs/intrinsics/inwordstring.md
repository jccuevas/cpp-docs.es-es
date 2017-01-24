---
title: "__inwordstring | Microsoft Docs"
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
  - "__inwordstring"
  - "__inwordstring_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__inwordstring (función intrínseca)"
  - "rep insw (instrucción)"
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __inwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Lee datos de puerto especificado mediante la instrucción de `rep insw` .  
  
## Sintaxis  
  
```  
void __inwordstring(  
   unsigned short Port,  
   unsigned short* Buffer,  
   unsigned long Count  
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto de lectura.  
  
 \[out\] `Buffer`  
 Los datos leídos de puerto se escribe aquí.  
  
 \[in\] `Count`  
 El número de palabras de datos a la lectura.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__inwordstring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)