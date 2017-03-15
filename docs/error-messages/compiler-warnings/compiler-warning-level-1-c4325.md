---
title: "Advertencia del compilador (nivel 1) C4325 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4325"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4325"
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4325
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**se han omitido los atributos para la sección estándar '**   
 ***sección* '**  
  
 No es posible cambiar los atributos de una sección estándar.  Por ejemplo:  
  
```  
#pragma section(".sdata", long)  
```  
  
 De esta forma, se reemplazaría la sección estándar `.sdata` que utiliza el tipo de datos **short** por el tipo de datos **long**.  
  
 Las secciones estándar cuyos atributos no se pueden cambiar comprenden:  
  
-   .data  
  
-   .sdata  
  
-   .bss  
  
-   .sbss  
  
-   .text  
  
-   .const  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 Pueden agregarse secciones adicionales más adelante.  
  
## Vea también  
 [section](../../preprocessor/section.md)