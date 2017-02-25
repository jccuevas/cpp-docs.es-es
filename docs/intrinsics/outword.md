---
title: "__outword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__outword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__outword (función intrínseca)"
  - "out (instrucción)"
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __outword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `out` , que manda la palabra `Data` el puerto de E\/S especificado por `Port`.  
  
## Sintaxis  
  
```  
void __outword(   
   unsigned short Port,   
   unsigned short Data   
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto para enviar los datos a.  
  
 \[in\] `Data`  
 Los datos que se envían.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__outword`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)