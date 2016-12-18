---
title: "__sidt | Microsoft Docs"
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
  - "__sidt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sidt (instrucción)"
  - "__sidt (función intrínseca)"
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __sidt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Almacena el valor del registro \(IDTR\) de la tabla del descriptor de la interrupción en la ubicación de memoria especificada.  
  
## Sintaxis  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `Destination`|Un puntero a la ubicación de memoria donde se almacena el IDTR.|  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__sidt`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 La función de `__sidt` es equivalente a la instrucción máquina de `SIDT` .  Para obtener más información, busque el documento, “Manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones,” en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_lidt](../intrinsics/lidt.md)