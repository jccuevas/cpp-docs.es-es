---
title: "__inbytestring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__inbytestring"
  - "__inbytestring_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep insb (instrucción)"
  - "__inbytestring (función intrínseca)"
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __inbytestring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Lee datos de puerto especificado mediante la instrucción de `rep insb` .  
  
## Sintaxis  
  
```  
void __inbytestring(  
   unsigned short Port,  
   unsigned char* Buffer,  
   unsigned long Count  
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto de lectura.  
  
 \[out\] `Buffer`  
 Los datos leídos de puerto se escribe aquí.  
  
 \[in\] `Count`  
 El número de bytes de datos que se van a leer.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__inbytestring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)