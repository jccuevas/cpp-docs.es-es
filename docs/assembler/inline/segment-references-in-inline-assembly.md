---
title: "Referencias a segmentos en los ensamblados alineados | Microsoft Docs"
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
helpviewer_keywords: 
  - "ensamblado en línea, registros"
  - "ensamblado en línea, referencias a segmentos"
  - "referencias, ensamblado en línea"
  - "registros"
  - "registros, ensamblado en línea"
  - "referencias a segmentos en ensamblado alineado"
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Referencias a segmentos en los ensamblados alineados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Debe hacer referencia a los segmentos por registro en lugar de por nombre \(el nombre de segmento `_TEXT` no es válido, por ejemplo\).  Los reemplazos de segmento deben usar el registro explícitamente, como en ES:\[BX\].  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Usar lenguaje de ensamblado en bloques \_\_asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)