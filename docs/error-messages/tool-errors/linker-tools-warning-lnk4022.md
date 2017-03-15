---
title: "Advertencia de las herramientas del vinculador LNK4022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4022"
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia de las herramientas del vinculador LNK4022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no puede se encontrar una coincidencia única para el símbolo 'símbolo'  
  
 Las herramientas LINK o LIB encontraron múltiples coincidencias para el símbolo no representativo dado, y no se pudo resolver la ambigüedad.  No se genera ningún archivo de salida \(.exe, .dll o .lib\).  Esta advertencia va seguida de otra advertencia [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) por cada símbolo duplicado y del error irrecuperable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).  
  
 Para evitar esta advertencia, especifique el símbolo en su forma decorada.  Ejecute [DUMPBIN](../../build/reference/dumpbin-options.md) en el objeto para ver los nombres representativos.