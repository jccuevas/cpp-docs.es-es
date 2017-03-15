---
title: "__outdwordstring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__outdwordstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "outsd (instrucción)"
  - "__outdwordstring (función intrínseca)"
  - "rep outsd (instrucción)"
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __outdwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucciónde `rep outsd`, que envía las palabras dobles de `Count` que comienzan en `Buffer` desproteger el puerto de E\/S especificado por `Port`.  
  
## Sintaxis  
  
```  
void __outdwordstring(   
   unsigned short Port,   
   unsigned long* Buffer,   
   unsigned long Count   
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto para enviar los datos a.  
  
 \[in\] `Buffer`  
 Un puntero a los datos que se envían el puerto especificado.  
  
 \[in\] `Count`  
 El número de palabras dobles a enviar.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__outdwordstring`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)