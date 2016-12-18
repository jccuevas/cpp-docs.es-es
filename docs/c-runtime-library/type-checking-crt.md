---
title: "Comprobaci&#243;n de tipos (CRT) | Microsoft Docs"
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
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "comprobación de tipo"
  - "comprobación de tipos"
  - "funciones de argumentos de variables"
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Comprobaci&#243;n de tipos (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El compilador realiza la comprobación de tipos limitada en las funciones que pueden tomar un número variable de argumentos, como sigue:  
  
|Llamada a función|Argumentos Tipo\-comprobados|  
|-----------------------|----------------------------------|  
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|Primer argumento \(cadena de formato\)|  
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|Primeros dos argumentos \(archivo o búfer y cadena de formato\)|  
|`_snprintf_s`|Tres primeros argumentos \(archivo o búfer, recuento, y una cadena de formato\)|  
|`_open`|Primeros dos argumentos \(ruta y marca de `_open` \)|  
|`_sopen_s`|Tres primeros argumentos \(ruta, marcador de `_open` , y modo compartido\)|  
|`_execl`, `_execle`, `_execlp`, `_execlpe`|Primeros dos argumentos \(ruta y primer puntero de argumento\)|  
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|Tres primeros argumentos \(indicador de modo, ruta, y primer puntero de argumento\)|  
  
 El compilador realiza la misma comprobación de tipo limitada en sus homólogos de caracteres anchos de estas funciones.  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)