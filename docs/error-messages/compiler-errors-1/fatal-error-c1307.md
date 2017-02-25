---
title: "Error irrecuperable C1307 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1307"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1307"
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable C1307
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el programa se ha editado desde que se recogieron los datos de perfil  
  
 Al utilizar [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el vinculador detectó un módulo de entrada recopilado a continuación de \/LTCG:PGINSTRUMENT y que el módulo se modificó hasta el punto que los datos de perfil existentes ya no son relevantes.  Por ejemplo, si el gráfico de llamadas cambió en el módulo recompilado, el compilador generará el error C1307.  
  
 Para resolver este error, ejecute \/LTCG: PGINSTRUMENT, vuelva a realizar todas las ejecuciones de prueba y ejecute \/LTCG: PGOPTIMIZE.  Si no puede ejecutar \/LTCG: PGINSTRUMENT y vuelve a realizar todas las ejecuciones de prueba, utilice \/LTCG: PGUPDATE en lugar de \/LTCG: PGOPTIMIZE para crear la imagen optimizada.