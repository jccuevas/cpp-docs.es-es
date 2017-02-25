---
title: "__outwordstring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__outwordstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep outsw (instrucción)"
  - "__outwordstring (función intrínseca)"
  - "outsw (instrucción)"
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __outwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `rep outsw` , que envía las palabras de `Count` que comienzan en `Buffer` desproteger el puerto de E\/S especificado por `Port`.  
  
## Sintaxis  
  
```  
void __outwordstring(   
   unsigned short Port,   
   unsigned short* Buffer,   
   unsigned long Count   
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto para enviar los datos a.  
  
 \[in\] `Buffer`  
 Un puntero a los datos que se envían el puerto especificado.  
  
 \[in\] `Count`  
 El número de palabras a enviar.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__outwordstring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)