---
title: "Error de las herramientas del vinculador LNK1188 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1188"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1188"
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error de las herramientas del vinculador LNK1188
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BADFIXUPSECTION:: destino de corrección 'símbolo' no válido; posiblemente sección de longitud cero  
  
 Durante una vinculación de VxD, el destino de una reubicación no tenía una sección.  Con LINK386 \(una versión anterior\), puede haberse utilizado un registro OMF GROUP \(generado por una directiva MASM GROUP\) para combinar la sección de longitud cero con otra sección de longitud no cero.  El formato COFF no admite la directiva GROUP ni las secciones de longitud cero.  Cuando LINK convierte automáticamente este tipo de objetos OMF a COFF, puede producirse este error.