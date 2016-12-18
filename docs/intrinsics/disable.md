---
title: "_disable | Microsoft Docs"
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
  - "_disable_cpp"
  - "_disable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_disable intrinsic"
  - "disable intrinsic"
  - "rsm instruction"
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _disable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Deshabilita las interrupciones.  
  
## Sintaxis  
  
```  
void _disable(void);  
```  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`_disable`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 `_disable` indica al procesador que debe borrar la marca de la interrupción.  En sistemas x86, esta función genera la instrucción Borrar marca de interrupción \(`cli`\).  
  
 Esta función solo está disponible en modo kernel.  Si se utiliza en modo de usuario, se produce una excepción de Instrucción privilegiada en tiempo de ejecución.  
  
 En las plataformas ARM, esta rutina solo está disponible como intrínseco.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)