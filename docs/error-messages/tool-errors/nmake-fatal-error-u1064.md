---
title: "Error grave de NMAKE U1064 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1064"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1064"
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error grave de NMAKE U1064
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se encontró ningún archivo MAKE y no se especificó ningún destino  
  
 La línea de comandos de NMAKE no ha especificado ningún archivo MAKE ni ningún destino, y el directorio actual no contiene ningún archivo denominado MAKE.  
  
 NMAKE requiere un archivo MAKE o un destino de línea de comandos \(o ambos\).  Para que NMAKE tenga disponible un archivo MAKE, especifique la opción \/F o coloque un archivo denominado MAKE en el directorio actual.  NMAKE puede crear un destino de línea de comandos utilizando una regla de inferencia si no se proporciona un archivo MAKE.