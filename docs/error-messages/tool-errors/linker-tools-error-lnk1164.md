---
title: "Error de las herramientas del vinculador LNK1164 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1164"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1164"
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error de las herramientas del vinculador LNK1164
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Alineación de la sección de la sección \(número\) mayor que el valor \/ALIGN  
  
 El tamaño de alineación de la sección dada del archivo objeto supera el valor especificado en la opción [\/ALIGN](../../build/reference/align-section-alignment.md).  El valor **\/ALIGN** debe ser una potencia de 2 igual o superior a la alineación de sección especificada en el archivo objeto.  
  
 Vuelva a compilar con una alineación inferior o aumente el valor de **\/ALIGN**.