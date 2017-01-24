---
title: "__outdword | Microsoft Docs"
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
  - "__outdword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out (instrucción)"
  - "outdword (instrucción)"
  - "__outdword (función intrínseca)"
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __outdword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `out` de texto una palabra doble `Data` el puerto `Port`.  
  
## Sintaxis  
  
```  
void __outdword(   
   unsigned short Port,   
   unsigned long Data   
);  
```  
  
#### Parámetros  
 \[in\] `Port`  
 El puerto para enviar los datos a.  
  
 \[in\] `Data`  
 La doble palabra que se va a enviar.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`__outdword`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)