---
title: "Error de las herramientas del vinculador LNK1264 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1264"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1264"
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1264
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se especificó \/LTCG:PGINSTRUMENT pero no se requiere generación de código; error de instrumentación  
  
 Se especificó **\/LTCG:PGINSTRUMENT** pero no se hallaron archivos .obj compilados con [\/GL](../../build/reference/gl-whole-program-optimization.md).  La instrumentación no puede tener lugar y se produce un error de vinculación.  Debe haber al menos un archivo .obj en la línea de comandos que se compile con **\/GL** para que pueda tener lugar la instrumentación.  
  
 La optimización guiada por perfiles \(PGO\) sólo está disponible en compiladores de 64 bits.