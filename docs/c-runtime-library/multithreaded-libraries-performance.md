---
title: "Rendimiento de bibliotecas multiproceso | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bibliotecas, con subprocesamiento múltiple"
  - "bibliotecas multiproceso"
  - "rendimiento, multithreading"
  - "subprocesamiento [C++], rendimiento"
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Rendimiento de bibliotecas multiproceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

CRT con un único subproceso deja de estar disponible.  En este tema se explica cómo obtener el máximo rendimiento de las bibliotecas multiproceso.  
  
## Maximizar el rendimiento  
 El rendimiento de las bibliotecas multiproceso se ha mejorado y está cercano al rendimiento de las bibliotecas de un único subproceso ahora\- eliminado.  Para aquellas situaciones incluso cuando se requiere un mayor rendimiento, hay varias características nuevas.  
  
-   El bloqueo independiente de la secuencia permite bloquear una secuencia y después que utilice [\_nolock \(Funciones\)](../c-runtime-library/nolock-functions.md) que tenga acceso a la secuencia directamente.  Esto permite que el uso de bloqueo hay bucles críticos alzados externo.  
  
-   La configuración regional de Por\- subproceso reduce el costo de acceso de la configuración regional para escenarios multiproceso \(vea [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)\).  
  
-   Las funciones Configuración regional\- dependientes \(con los nombres finalizando en \_l\) usan la configuración regional como parámetro, quitando el costo sustancial \(por ejemplo, [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\).  
  
-   Las optimizaciones para los codepages comunes reduce el costo de muchas operaciones cortas.  
  
-   Definir [\_CRT\_DISABLE\_PERFCRIT\_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) fuerza todas las operaciones de E\/S adopte un modelo con un único subproceso de E\/S y utilizar los formularios de \_nolock de funciones.  Esto permite muy a I\/O\-based aplicaciones de un único subproceso para obtener un mejor rendimiento.  
  
-   La exposición del identificador del montón de CRT permite habilitar la pila \(LFH\) de Windows Bajo Fragmentation para el montón de CRT, lo que puede mejorar notablemente el rendimiento en escenarios muy soliciten.  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)