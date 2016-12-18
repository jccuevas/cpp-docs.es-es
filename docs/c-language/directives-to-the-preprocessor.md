---
title: "Directivas para el preprocesador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Directivas para el preprocesador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una “directiva” indica al preprocesador de C que realice una acción concreta en el texto del programa antes de la compilación.  Las [directivas de preprocesador](../preprocessor/preprocessor-directives.md) se describen con detalle en la *referencia del preprocesador*.  En el ejemplo siguiente se usa la directiva de preprocesador `#define`:  
  
```  
#define MAX 100  
```  
  
 Esta instrucción indica al compilador que reemplace cada aparición de `MAX` por `100` antes de la compilación.  Las directivas de preprocesador del compilador de C son:  
  
|\#define|\#endif|\#ifdef|\#line|  
|--------------|-------------|-------------|------------|  
|`#elif`|`#error`|**\#ifndef**|**\#pragma**|  
|`#else`|`#if`|`#include`|`#undef`|  
  
## Vea también  
 [Archivos de código fuente y programas de origen](../c-language/source-files-and-source-programs.md)