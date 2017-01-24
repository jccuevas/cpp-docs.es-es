---
title: "__lidt | Microsoft Docs"
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
  - "__lidt"
  - "__lidt_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LIDT (instrucción)"
  - "__lidt (función intrínseca)"
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __lidt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Carga el registro de la tabla del descriptor de la interrupción \(IDTR\) con el valor en la ubicación de memoria especificada.  
  
## Sintaxis  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|\[in\] `Source`|Puntero al valor que se copien en el IDTR.|  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__lidt`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 La función de `__lidt` es equivalente a la instrucción máquina de `LIDT` , y está disponible únicamente en modo kernel.  Para obtener más información, busque el documento, “Manual del desarrollador de software de arquitectura Intel, volumen 2: Referencia del conjunto de instrucciones,” en [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) el sitio.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [\_\_sidt](../intrinsics/sidt.md)